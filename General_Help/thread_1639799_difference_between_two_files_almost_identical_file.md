---
title: "difference between two files almost identical files"
date: 2010-12-07
forum: General Help
---

### Post by COKEDUDE on 2010-12-07
I am trying to compare the difference between 2 ALMOST identical. Yes I know about the diff and sdiff command. The problem is with how similar they are it is VERY hard to see the difference.  Here is my output if you want to see for yourself. 
```
~ $ diff /home/bob/Downloads/omega.contacts.msn.com /home/bob/.purple/certificates/x509/tls_peers/omega.contacts.msn.com
1c1
< -----BEGIN CERTIFICATE-----
---
> -----BEGIN CERTIFICATE-----
36,37c36,37
< 7w3bhyHPFr+/13BCIWSfKnSRj/g6YoHnhF4gyQ==
< -----END CERTIFICATE-----
---
> 7w3bhyHPFr+/13BCIWSfKnSRj/g6YoHnhF4gyQ==
> -----END CERTIFICATE-----

```

Here are the files in code tags. 
```
-----BEGIN CERTIFICATE-----

MIIGeDCCBWCgAwIBAgIKfdrgSQAIAAHIuTANBgkqhkiG9w0BAQUFADCBizETMBEG

CgmSJomT8ixkARkWA2NvbTEZMBcGCgmSJomT8ixkARkWCW1pY3Jvc29mdDEUMBIG

CgmSJomT8ixkARkWBGNvcnAxFzAVBgoJkiaJk/IsZAEZFgdyZWRtb25kMSowKAYD

VQQDEyFNaWNyb3NvZnQgU2VjdXJlIFNlcnZlciBBdXRob3JpdHkwHhcNMTAxMTE1

MjEyODE5WhcNMTIxMTE0MjEyODE5WjB2MQswCQYDVQQGEwJVUzELMAkGA1UECBMC

V0ExEDAOBgNVBAcTB1JlZG1vbmQxDDAKBgNVBAoTA01TTjEdMBsGA1UECxMUTVNO

IENvbnRhY3QgU2VydmljZXMxGzAZBgNVBAMMEiouY29udGFjdHMubXNuLmNvbTCC

ASIwDQYJKoZIhvcNAQEBBQADggEPADCCAQoCggEBAJnXhdENETaZ8YFfenWCuky3

Fke/oWgUOEbgvaRuZusd2LnvoSiqH++2lkV0JJlIQ+7jLLN8MY7VhlHQmkLC3x44

KZn2IktMVgTBGMKnvbyYVAnRsjt/rVhQrQeHVEQzv5WXx//3FKmXWAuJiuRj9PZ2

KsNqPJgaaa5cuOu4oynO9fH5/ZtJIeUf7bC4Wu++o7jTu5zOhIa7R1buE9FXFF33

vQ1vHi4p9zR2Pi/i2nUpEnzeNCLl/8F/Tf+658SvIC4EzxrYcj+fit6sAnNUfsOE

1SIk9YLD+tS0fln1afbcDvH0ib5Xm7u2/o6ZmxQU0mrAkfQectsKpZLJj03neBsC

AwEAAaOCAvAwggLsMAsGA1UdDwQEAwIEsDBEBgkqhkiG9w0BCQ8ENzA1MA4GCCqG

SIb3DQMCAgIAgDAOBggqhkiG9w0DBAICAIAwBwYFKw4DAgcwCgYIKoZIhvcNAwcw

HQYDVR0lBBYwFAYIKwYBBQUHAwIGCCsGAQUFBwMBMB0GA1UdDgQWBBRciAVJ/Vsj

sAlZoNG/Zs+rILsPNDAfBgNVHSMEGDAWgBQIQuPbThFm87UIxUDbVXwzRhGDODCC

AQoGA1UdHwSCAQEwgf4wgfuggfiggfWGWGh0dHA6Ly9tc2NybC5taWNyb3NvZnQu

Y29tL3BraS9tc2NvcnAvY3JsL01pY3Jvc29mdCUyMFNlY3VyZSUyMFNlcnZlciUy

MEF1dGhvcml0eSg4KS5jcmyGVmh0dHA6Ly9jcmwubWljcm9zb2Z0LmNvbS9wa2kv

bXNjb3JwL2NybC9NaWNyb3NvZnQlMjBTZWN1cmUlMjBTZXJ2ZXIlMjBBdXRob3Jp

dHkoOCkuY3JshkFodHRwOi8vY29ycHBraS9jcmwvTWljcm9zb2Z0JTIwU2VjdXJl

JTIwU2VydmVyJTIwQXV0aG9yaXR5KDgpLmNybDCBvwYIKwYBBQUHAQEEgbIwga8w

XgYIKwYBBQUHMAKGUmh0dHA6Ly93d3cubWljcm9zb2Z0LmNvbS9wa2kvbXNjb3Jw

L01pY3Jvc29mdCUyMFNlY3VyZSUyMFNlcnZlciUyMEF1dGhvcml0eSg4KS5jcnQw

TQYIKwYBBQUHMAKGQWh0dHA6Ly9jb3JwcGtpL2FpYS9NaWNyb3NvZnQlMjBTZWN1

cmUlMjBTZXJ2ZXIlMjBBdXRob3JpdHkoOCkuY3J0MD8GCSsGAQQBgjcVBwQyMDAG

KCsGAQQBgjcVCIPPiU2t8gKFoZ8MgvrKfYHh+3SBT4PC7YUIjqnShWMCAWQCAQow

JwYJKwYBBAGCNxUKBBowGDAKBggrBgEFBQcDAjAKBggrBgEFBQcDATANBgkqhkiG

9w0BAQUFAAOCAQEAbbWUY/5r/Tv/kefqNUT5aGVejrkbG4229gnJLcv+uQTEg0Gg

xfvLr77N1z2j57FameJwz6DeTRbK8MYVPoP+z5o4vM3F3GxLm7aBklYQ/7G0TIp/

13z01a5aBGvZH8umzex3YrAnhJEcucSN5WaT6r9uwT7imdbsCgfFPdiIgS5iHdcl

k/3QSpau+4/XZgh/8V/FMN9KEFYGvEhMb5EVzKJ8pqF9Jy9Mfzqev3BtSREiljCt

lJuiRamxWgQoeNVTAI+J2YAsD8Qon1iZiHl08uHdgXWZiGDtLPcd9aIiL7/vi/+D

7w3bhyHPFr+/13BCIWSfKnSRj/g6YoHnhF4gyQ==

-----END CERTIFICATE-----
```

```
-----BEGIN CERTIFICATE-----
MIIGeDCCBWCgAwIBAgIKfdrgSQAIAAHIuTANBgkqhkiG9w0BAQUFADCBizETMBEG

CgmSJomT8ixkARkWA2NvbTEZMBcGCgmSJomT8ixkARkWCW1pY3Jvc29mdDEUMBIG

CgmSJomT8ixkARkWBGNvcnAxFzAVBgoJkiaJk/IsZAEZFgdyZWRtb25kMSowKAYD

VQQDEyFNaWNyb3NvZnQgU2VjdXJlIFNlcnZlciBBdXRob3JpdHkwHhcNMTAxMTE1

MjEyODE5WhcNMTIxMTE0MjEyODE5WjB2MQswCQYDVQQGEwJVUzELMAkGA1UECBMC

V0ExEDAOBgNVBAcTB1JlZG1vbmQxDDAKBgNVBAoTA01TTjEdMBsGA1UECxMUTVNO

IENvbnRhY3QgU2VydmljZXMxGzAZBgNVBAMMEiouY29udGFjdHMubXNuLmNvbTCC

ASIwDQYJKoZIhvcNAQEBBQADggEPADCCAQoCggEBAJnXhdENETaZ8YFfenWCuky3

Fke/oWgUOEbgvaRuZusd2LnvoSiqH++2lkV0JJlIQ+7jLLN8MY7VhlHQmkLC3x44

KZn2IktMVgTBGMKnvbyYVAnRsjt/rVhQrQeHVEQzv5WXx//3FKmXWAuJiuRj9PZ2

KsNqPJgaaa5cuOu4oynO9fH5/ZtJIeUf7bC4Wu++o7jTu5zOhIa7R1buE9FXFF33

vQ1vHi4p9zR2Pi/i2nUpEnzeNCLl/8F/Tf+658SvIC4EzxrYcj+fit6sAnNUfsOE

1SIk9YLD+tS0fln1afbcDvH0ib5Xm7u2/o6ZmxQU0mrAkfQectsKpZLJj03neBsC

AwEAAaOCAvAwggLsMAsGA1UdDwQEAwIEsDBEBgkqhkiG9w0BCQ8ENzA1MA4GCCqG

SIb3DQMCAgIAgDAOBggqhkiG9w0DBAICAIAwBwYFKw4DAgcwCgYIKoZIhvcNAwcw

HQYDVR0lBBYwFAYIKwYBBQUHAwIGCCsGAQUFBwMBMB0GA1UdDgQWBBRciAVJ/Vsj

sAlZoNG/Zs+rILsPNDAfBgNVHSMEGDAWgBQIQuPbThFm87UIxUDbVXwzRhGDODCC

AQoGA1UdHwSCAQEwgf4wgfuggfiggfWGWGh0dHA6Ly9tc2NybC5taWNyb3NvZnQu

Y29tL3BraS9tc2NvcnAvY3JsL01pY3Jvc29mdCUyMFNlY3VyZSUyMFNlcnZlciUy

MEF1dGhvcml0eSg4KS5jcmyGVmh0dHA6Ly9jcmwubWljcm9zb2Z0LmNvbS9wa2kv

bXNjb3JwL2NybC9NaWNyb3NvZnQlMjBTZWN1cmUlMjBTZXJ2ZXIlMjBBdXRob3Jp

dHkoOCkuY3JshkFodHRwOi8vY29ycHBraS9jcmwvTWljcm9zb2Z0JTIwU2VjdXJl

JTIwU2VydmVyJTIwQXV0aG9yaXR5KDgpLmNybDCBvwYIKwYBBQUHAQEEgbIwga8w

XgYIKwYBBQUHMAKGUmh0dHA6Ly93d3cubWljcm9zb2Z0LmNvbS9wa2kvbXNjb3Jw

L01pY3Jvc29mdCUyMFNlY3VyZSUyMFNlcnZlciUyMEF1dGhvcml0eSg4KS5jcnQw

TQYIKwYBBQUHMAKGQWh0dHA6Ly9jb3JwcGtpL2FpYS9NaWNyb3NvZnQlMjBTZWN1

cmUlMjBTZXJ2ZXIlMjBBdXRob3JpdHkoOCkuY3J0MD8GCSsGAQQBgjcVBwQyMDAG

KCsGAQQBgjcVCIPPiU2t8gKFoZ8MgvrKfYHh+3SBT4PC7YUIjqnShWMCAWQCAQow

JwYJKwYBBAGCNxUKBBowGDAKBggrBgEFBQcDAjAKBggrBgEFBQcDATANBgkqhkiG

9w0BAQUFAAOCAQEAbbWUY/5r/Tv/kefqNUT5aGVejrkbG4229gnJLcv+uQTEg0Gg

xfvLr77N1z2j57FameJwz6DeTRbK8MYVPoP+z5o4vM3F3GxLm7aBklYQ/7G0TIp/

13z01a5aBGvZH8umzex3YrAnhJEcucSN5WaT6r9uwT7imdbsCgfFPdiIgS5iHdcl

k/3QSpau+4/XZgh/8V/FMN9KEFYGvEhMb5EVzKJ8pqF9Jy9Mfzqev3BtSREiljCt

lJuiRamxWgQoeNVTAI+J2YAsD8Qon1iZiHl08uHdgXWZiGDtLPcd9aIiL7/vi/+D

7w3bhyHPFr+/13BCIWSfKnSRj/g6YoHnhF4gyQ==
-----END CERTIFICATE-----
```

Here are download links so you can compare them yourselves. 
[http://www.mediafire.com/?tvbb86y6m7361m6](http://www.mediafire.com/?tvbb86y6m7361m6)
[http://www.mediafire.com/?g883kkdb2oqr3r8](http://www.mediafire.com/?g883kkdb2oqr3r8)

Could I get some recommendations on how to see the difference's between these 2 files. I wanna know if there is like a extra space on one line, a different formatting, a capital or lowercase letter, etc. I want to know what the specific differences are.

---

### Post by surfer on 2010-12-07
meld or kompare are graphic tools that may show a little more detail.

---

