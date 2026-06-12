---
title: "Juniper Network Connect Times out"
date: 2010-08-26
forum: General Help
---

### Post by The Desert Fox on 2010-08-26
Hi All

I am running 9.10 with Sun Java 6 JDK. I can connect to my company's network using Juniper Network Connect, however it displays a "Session Timeout" after 10 minutes or so, even though I am actively using the network. 

Does anyone have any ides? Is there any way I can get any debug information? My company's IT people are clueless about Linux... just as clueless as they are about everything else.

---

### Post by spleach on 2010-10-07
This happens with me all the time too... Apparently there's a Juniper NC version 7 (I'm running 6.5), but Juniper doesn't provide it directly and my uni's web service doesn't seem to upgrade it automatically. loooooong

---

### Post by =CrAzYG33K= on 2011-04-16
My Univ VPN has this same time-out issue too.

However, for me it'd allow only 1sec/2secs. It then times out :(.
Any solutions to this?

**EDIT:**

Found the solution: There is some kind of mismatch between OpenJDK and Juniper. Solution is to uninstall OpenJDK completely and install Sun Java (Java6) as described here :
[http://www.juniperforum.com/index.php?topic=10394.0](http://www.juniperforum.com/index.php?topic=10394.0)

It worked for me! :)

---

