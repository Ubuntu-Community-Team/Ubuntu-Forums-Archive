---
title: "Sybase ASE 15.5 startup error"
date: 2011-10-24
forum: General Help
---

### Post by ubuntu-user on 2011-10-24
While starting up the ASE server with command :

**$startserver -f RUN_SYBASE_ASE**

I am getting error 'SYBASE_ASE' environment variable is not set and server is denying to start as it takes default path '/home/sybase/ASE-15_0' which in fact does not exists, but when checked with command :

**$ echo $SYBASE_ASE**

I can see the out put :

**/opt/sybase/ASE-15_0/**

Any idea on how to resolve this error ?

---

### Post by ubuntu-user on 2011-10-24
This is the error :

[COLOR=Purple]sybase@pc:/opt/sybase/ASE-15_0/install$ 00:00:00000:00000:2011/10/25 08:07:46.74 kernel  Warning: [COLOR=Red]Environment variable SYBASE_ASE is not set.[/COLOR]
00:00:00000:00000:2011/10/25 08:07:47.06 kernel  SySAM: Using licenses from: /usr/local/flexlm/licenses/license.dat
00:00:00000:00000:2011/10/25 08:07:47.06 kernel  SySAM: Failed to get status of file [COLOR=Red]/home/sybase/ASE-15_0/sysam/SYBASE_ASE[/COLOR].properties. errno=2 No such file or directory.
00:00:00000:00000:2011/10/25 08:07:47.06 kernel  SySAM: Failed to open /home/sybase/ASE-15_0/sysam/SYBASE_ASE.properties file: errno=2 No such file or directory.
00:00:00000:00000:2011/10/25 08:07:47.06 kernel  License manager initialization fails.
00:00:00000:00000:2011/10/25 08:07:47.06 kernel  There is no valid license for ASE server product. Installation date is not found or installation grace period has expired. Server will not boot.[/COLOR]

But when cross checked :

[B]sybase@pc:/opt/sybase/ASE-15_0/install$ [COLOR=Purple]echo $SYBASE_ASE[/COLOR]
/opt/sybase/ASE-15_0[/B]
[B]sybase@pc:/opt/sybase/ASE-15_0/install$ [COLOR=Purple]echo $SYBASE_ASE[/COLOR]
/opt/sybase/ASE-15_0
sybase@pc:/opt/sybase/ASE-15_0/install$ [COLOR=Purple]echo $SYBASE_OCS[/COLOR]
/opt/sybase/OCS-15_0
sybase@pc:/opt/sybase/ASE-15_0/install$ [COLOR=Purple]echo $SYBASE[/COLOR]
/opt/sybase[/B]

The startserver is trying to look up the license in '/home/sybase/ASE-15_0/SySam' , which is actually at '/opt/sybase/ASE-15_0/SySam'

---

