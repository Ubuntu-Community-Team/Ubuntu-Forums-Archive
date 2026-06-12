---
title: "Java 7 plugin out of date?"
date: 2011-11-26
forum: General Help
---

### Post by TennSeven on 2011-11-26
Hi all,

I am trying to move to Oracle's JRE from openjdk (I need a java console in my browser plugin so I can debug programs, and the iced-tea plugin doesn't have one).  I am running version 11.10 x64.

I downloaded Oracle's package, extracted it and put it into /usr/lib/jvm.  Then I ran a script I found somewhere that was supposed to set everything up (it didn't change the JAVA_HOME variable, but everything else looks kosher).  Afterwards, I created a "plugins" directory in /opt/google/chrome and threw in a link to /usr/lib/jvm/java-7-oracle/lib/amd64/libnpjp2.so.

Now the plugin shows up in Chrome's plugin list as version 1.7.0 but it includes a link that says "Download Critical Security Update."  Likewise, when I try to load an applet Chrome will tell me that the plugin is out of date and offer a link to upgrade it.  Clicking on either link brings me to Oracle's download page for java version 6, update 29 (the download page for the entire JRE, not just the plugin).

Replacing the link to the 1.7 plugin with one to 1.6 gets rid of the "Download Critical Security Update" in the Chrome plugins list, but it still will not run applets, saying the plugin is out of date (in either case, telling Chrome to run the applet anyway yields no results).

What did I mess up?

---

### Post by oldtimer7777 on 2011-11-26
Did you try a walkthrough like this:

[https://debianhelp.wordpress.com/2011/11/13/how-to-install-sun-java-se-1-7/](https://debianhelp.wordpress.com/2011/11/13/how-to-install-sun-java-se-1-7/)

> **TennSeven said:**
> Hi all,

I am trying to move to Oracle's JRE from openjdk (I need a java console in my browser plugin so I can debug programs, and the iced-tea plugin doesn't have one).  I am running version 11.10 x64.

I downloaded Oracle's package, extracted it and put it into /usr/lib/jvm.  Then I ran a script I found somewhere that was supposed to set everything up (it didn't change the JAVA_HOME variable, but everything else looks kosher).  Afterwards, I created a "plugins" directory in /opt/google/chrome and threw in a link to /usr/lib/jvm/java-7-oracle/lib/amd64/libnpjp2.so.

Now the plugin shows up in Chrome's plugin list as version 1.7.0 but it includes a link that says "Download Critical Security Update."  Likewise, when I try to load an applet Chrome will tell me that the plugin is out of date and offer a link to upgrade it.  Clicking on either link brings me to Oracle's download page for java version 6, update 29 (the download page for the entire JRE, not just the plugin).

Replacing the link to the 1.7 plugin with one to 1.6 gets rid of the "Download Critical Security Update" in the Chrome plugins list, but it still will not run applets, saying the plugin is out of date (in either case, telling Chrome to run the applet anyway yields no results).

What did I mess up?

---

### Post by TennSeven on 2011-11-27
Oldtimer,

That is exactly the tutorial I followed, as outlined in my post, except that I added the plugin link into a different directory (it doesn't work either way).

---

