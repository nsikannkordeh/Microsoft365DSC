﻿# TeamsPstnUsage

## Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| **Usage** | Key | String | An online PSTN usage (such as Local or Long Distance) that can be used in conjunction with voice routes and voice routing policies. ||
| **Ensure** | Write | String | Present ensures the policy exists, absent ensures it is removed. |Present, Absent|
| **Credential** | Write | PSCredential | Credentials of the Teams Admin ||
| **ApplicationId** | Write | String | Id of the Azure Active Directory application to authenticate with. ||
| **TenantId** | Write | String | Name of the Azure Active Directory tenant used for authentication. Format contoso.onmicrosoft.com ||
| **CertificateThumbprint** | Write | String | Thumbprint of the Azure Active Directory application's authentication certificate to use for authentication. ||


# TeamsPstnUsage

### Description

This resource configures a Teams PSTN Usage.

More information: https://docs.microsoft.com/en-us/microsoftteams/direct-routing-voice-routing

## Examples

### Example 1

This example adds a new Teams PSTN Usage.

```powershell
Configuration Example
{
    param(
        [Parameter(Mandatory = $true)]
        [PSCredential]
        $credsGlobalAdmin
    )
    Import-DscResource -ModuleName Microsoft365DSC

    node localhost
    {
        TeamsPstnUsage 'ConfigurePstnUsage'
        {
            Usage      = 'Long Distance'
            Ensure     = 'Present'
            Credential = $credsGlobalAdmin
        }
    }
}
```

