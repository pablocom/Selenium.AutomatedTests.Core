# Selenium.AutomatedTests

[![CI](https://github.com/pablocom/Selenium.AutomatedTests/actions/workflows/buildAndRunUnitTests.yml/badge.svg)](https://github.com/pablocom/Selenium.AutomatedTests/actions/workflows/buildAndRunUnitTests.yml)

Easily write maintainable end-to-end tests using Selenium by writing automation scenarios in a fluent fashion.

It consists of a set of tools built atop existing features in Selenium.

## Installation
Install the library from [NuGet](https://www.nuget.org/packages/Selenium.AutomatedTests):
``` console
dotnet add package Selenium.AutomatedTests
```

## Example usage

```csharp
[Fact]
public void SearchForATextInGoogle()
{
    var builder = new AutomationScenarioBuilder(ProvideWebDriver());

    builder
        .NavigateTo("https://google.com")
        .WithSteps<GoogleSearchSteps>(step =>
        {
            step.WaitUntilSearchBarIsLoaded();
            step.ClickOnAcceptTermsAndConditions();
            step.Search("This is fine gif");
        });

    AutomationScenarioRunner.Run(builder);
}
```

Documentation: https://github.com/pablocom/Selenium.AutomatedTests/wiki
