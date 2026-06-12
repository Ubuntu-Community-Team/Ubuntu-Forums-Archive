---
title: "firefox: java plugin missing"
date: 2011-01-19
forum: General Help
---

### Post by stephan0h on 2011-01-19
Hi,

Recently it appeared to me that my java-plugin is missing. (apparently I don't need it that often). I've had various upgrades of firefox on my machine, currently i've got version 3.6.13.

I tried to check the plugin directory for the java-plugin - only to find out that I have more than one:
~/.mozilla/plugins
/usr/lib/firefox/plugins
/usr/lib/mozilla/plugins
/usr/lib/mozilla-firefox/plugins/
even a /usr/lib/firefox-addons/plugins/
... this is quite crazy.

I found out that the other plugins I use reside in /usr/lib/mozilla/plugins. In this directory there is a "libjavaplugin.so" pointing to "/etc/alternatives/mozilla-javaplugin.so". I made "/etc/alternatives/mozilla-javaplugin.so" point to "/usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so" (I read to do this in one of the numerous ubuntu wiki pages - before it was pointing to some java5 stuff). But this did not help.

All this has cost me hours now - but still I have no java-plugin. Quite frustrating.

Can someone help me please? How can I get a working java-plugin? How can I clean up all this plugin mess?

thanks,
stephan

---

### Post by uyulala on 2011-01-19
Hi,

the only thing in your description I do not recognize from my own machine is the name of the plugin file, I have

 /etc/alternatives/mozilla-javaplugin.so -> /usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so

The rest sounds right.

Hope this helps!

---

### Post by stephan0h on 2011-01-20
Hey thanks! This really solved it. 

I don't understand why I have so many plugin directories though.

---

