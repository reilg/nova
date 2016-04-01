# Nova
An express like framework for go web servers

Provides a lot of the same methods and functionality as express.js

Example
```go
n := nova.Nova()

//Static folder example
n.AddStatic("/sitedir/")

//Middleware Example
n.Use(func(req *nova.Request, res *nova.Response, next nova.Next) {
    res.R.Header().Set("Powered-By", "Nova")
    next()
})

//Route Examples
n.AddRoute("/test/taco/:apple", func(req *nova.Request, res *nova.Response) {
    res.Send("Received Taco")
});

n.AddRoute("/test/:taco/:apple", func(req *nova.Request, res *nova.Response) {
    res.Json(req.RouteParams)
});

err := n.Serve("8080")

if err != nil {
    log.Fatal(err)
}
```
# Todo:
Add graceful stopping