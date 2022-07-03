# Proinfocus ApiGateway

It is a simple library which adds Api Gateway functionality to your .NET 6 WebApi projects.

## NuGet Packages
Download NuGet package from [https://www.nuget.org/packages/Proinfocus.ApiGateway/]

## Usage
- Add **Proinfocus.ApiGateway** NuGet package to your .NET 6 WebApi project.
- Add the following lines in your `program.cs` file:
  - Declare the using statement at the top of the file:
    <br/>`using Proinfocus.ApiGateway;`
  - Add the following statement before the `var app = builder.Build();` line:
    <br/>`builder.AddApiGateway();`
  - Add the following statement before the `app.Run();` line:
    <br/>`app.UseApiGateway();`
  - Your minimalistic `program.cs` file should look like this:
    ```
    using Proinfocus.ApiGateway;
    
    var builder = WebApplication.CreateBuilder(args);
    builder.AddApiGateway();        
    var app = builder.Build();      
    app.UseApiGateway();
    app.Run();
    ```

- Add your ApiRoute settings in the `appsettings.json` file as follows:
  ```
    "ApiGatewayRoute": [
    {
        "routeName": "api/weather",
        "scheme": "https",
        "host": "localhost",
        "port": 7170
    },
    {
        "routeName": "api/auth",
        "scheme": "http",
        "host": "localhost",
        "port": 5193
    }]
  ```
- That's it! Now when you run this project (all other WebApi projects should already be running), you should be able to communicate with the endpoint of this project and get the desired outputs from the other WebApis running underhood.
