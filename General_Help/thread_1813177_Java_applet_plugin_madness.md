---
title: "Java applet plugin madness"
date: 2011-07-27
forum: General Help
---

### Post by KirbySmith on 2011-07-27
I'm using Firefox 3.6.18 on Ubuntu 10.04.2.  I'd like to get the console window on my ZyXEL router's web GUI to work.  By work I mean to be able to type into the window.  (The window no longer complains that Java isn't installed, or that it isn't initialized as it did under open Java.)  On-line Sun Java tester presently shows ... nothing.  About: plugins shows a myriad of java plugins, all enabled.  I have installed the latest Sun Java 1.6.0_26 using Synaptic, and have removed Iced Tea, which didn't work with open Java for getting the console window to function.  I have ensured that Sun Java is the operational version.

There are several threads on this forum that address various ways of installing Java that informed my steps up to now, but in trying to link in the correct file, I have run into unexpected terrain that the existing "cookbook" directions don't map out.

"usr/lib/jvm/java-6-sun/jre/lib/plugin/i386/ns7" contains "libjavaplugin_oji.so" which I would expect, extrapolating from the directions in these threads, to be the desired plugin.  Where to link it to, if anywhere?  What to remove, if anything?

"usr/lib/mozilla/plugins" contains "javaplugin.so", which is a link to "/etc/alternatives/mozilla-javaplugin.so", which in turn is a link to "/usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so" - a somewhat unexpected target.

usr/lib/firefox-3.6.18/plugins contains only a flash player related plugin.

Any help will be appreciated.

Thanks

kirby

---

