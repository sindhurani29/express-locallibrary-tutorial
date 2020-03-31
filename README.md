#MVC Application Execution Process
1. Request
1. The Route
1. The MvcHandler Executes
1. The controller Executes
1. Action Invoked

## Step 1 – Request
Receive first request for the application. In the Global.asax file
route objects are added to the Route table object. 

## Step 2 – The Route
The entry point for every MVC Application begins with Routing. After the application receives the request from the user, it uses URL Routing Module to handle the request. The RouteTable maps URLs to handlers.  Basically routing is a pattern matching system that matches the request’s URL against the URL patterns which is present in the Route Table. The Routing engine redirect the request to the corresponding IRouteHandler when the match found in the pattern. If corresponding requested URL not found in route table then it will return a 404 HTTP status code.

## Step 3 – The MvcHandler Executes
It is the responsibility of the RouteHandler to determine the HTTP handler that will serve the request, by looking at the received RequestContext. The RouteHandler object creates an instance of the MvcHandler class and passes the RequestContext instance to the handler.

RequestContext instance is used to identify the IControllerFactory object to create the controller instance.
The MvcHandler method calls the controller’s Execute method.

## Step 4 – The Controller Executes
The controller determines which action method to execute. MvcHandler uses IControllerFactory instance and to get IController object. Mvc controllers implement IController interface to execute the method which actually execute your action method.

## Step 5 – Action Invoked
After controller gets instantiated ActionInvoker will determines which Action method need to execute. ActionNameSelectorAttribute and ActionMethodSelectorAttribute methods used to select action method. The action method receives user input then executes the result and returning a result type to view. 

The result type can be ViewResult, RedirectToRouteResult, RedirectResult, ContentResult, JsonResult, FileResult, and EmptyResult. At last the view has been render to the browser as response.