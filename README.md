.NET Samples
Markdownlint

This repo contains all the sample code that is part of any topic under the .NET documentation. There are several different projects that are organized in sub-folders. These sub-folders are organized similarly to the organization of the docs for .NET. Some of the articles will have more than one sample associated with them.

The content team tracks issues for .NET documentation in the dotnet/docs and dotnet/dotnet-api-docs repositories. Issues are turned off on this repository. File issues against existing samples and suggestions for new samples in those repositories. If you're not sure where, choose dotnet/docs. This process keeps the issues associated with the articles that explain the concepts for each sample. The best process is to file an issue from the feedback control at the bottom of each docs page:

For existing samples, file the issue on the page with the sample.
To suggest new samples, file the issue on the index page where you want to see the new sample.
The code in this repository represents programs that demonstrate application or library scenarios. These samples often use more than one technology, feature, or toolkit. Each sample has a readme.md file that explains the sample and links to resources for more information.

Samples should be buildable projects. Those projects should build and run on the widest set of platforms possible for the given sample. In practice, that means building .NET Core-based console applications where possible. Samples that are specific to the web or a UI framework should add those tools as needed. Examples include web applications, mobile apps, WPF or WinForms apps, and so on.

We are working toward having a CI system in place for all code. When you make any updates to samples, make sure each update is part of a buildable project. Ideally, add tests for correctness on samples as well.

Building a sample
Build any .NET Core sample using the .NET Core CLI, which is installed with the .NET Core SDK. Then run these commands from the CLI in the directory of any sample:

dotnet build
dotnet run
These will install any needed dependencies, build the project, and run the project respectively.

Multi-project samples have instructions in their root directory in a README.md file.

Except where noted, all samples build from the command line on any platform supported by .NET Core. There are a few samples that are specific to Visual Studio and require Visual Studio 2017 or later. In addition, some samples show platform-specific features and will require a specific platform. Other samples and snippets require the .NET Framework and will run on Windows platforms, and will need the Developer Pack for the target Framework version.

Creating new samples
If you wish to add a code sample:

Your sample must be part of a buildable project. Where possible, the projects should build on all platforms supported by .NET Core. Exceptions to this are samples that demonstrate a platform-specific feature or platform-specific tool.

Your sample should conform to the runtime coding style to maintain consistency.

Additionally, we prefer the use of static methods rather than instance methods when demonstrating something that doesn't require instantiating a new object.
Your sample should include appropriate exception handling. It should handle all exceptions that are likely to be thrown in the context of the sample. For example, a sample that calls the Console.ReadLine method to retrieve user input should use appropriate exception handling when the input string is passed as an argument to a method. Similarly, if your sample expects a method call to fail, the resulting exception must be handled. Always handle the specific exceptions thrown by the method, rather than base class exceptions such as Exception or SystemException.

If your sample builds a standalone package, you must include the runtimes used by our CI build system, in addition to any runtimes used by your sample:

win7-x64
win8-x64
win81-x64
ubuntu.16.04-x64
We will have a CI system in place to build these projects shortly.

To create a sample:

File an issue or add a comment to an existing one that you are working on it.

Write the topic that explains the concepts demonstrated in your sample (example: docs/standard/linq/where-clause.md).

Write your sample (example: WhereClause-Sample1.cs).

Create a Program.cs with a Main entry point that calls your samples. If there is already one there, add the call to your sample:

public class Program
{
    public void Main(string[] args)
    {
        WhereClause1.QuerySyntaxExample();

        // Add the method syntax as an example.
        WhereClause1.MethodSyntaxExample();
    }
}
Don't check in the solution file if it contains only one project.

To build and run your sample:

Go to the sample folder and build to check for errors:

dotnet build
Run your sample:

dotnet run
Add a README.md to the root directory of your sample.

This should include a brief description of the code, and refer people to the article that references the sample.
