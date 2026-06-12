---
title: "shiretoko icedtea plugin"
date: 2010-03-08
forum: General Help
---

### Post by scarf on 2010-03-08
i have ubuntu 9.04 and i installed firefox-3.5 package AKA shiretoko.  i notice that it wasn't detecting/loading the icedtea java plugin (according to about:plugins), and i saw that /usr/lib/firefox/plugins/libjavaplugin.so was a broken link to /etc/alternatives/mozilla-javaplugin.so

so i issued the following commands:

```
cd /usr/lib/mozilla/plugins/
sudo rm libjavaplugin.so
sudo ln -s /usr/lib/jvm/java-6-openjdk/jre/lib/i386/IcedTeaPlugin.so ./libjavaplugin.so
```

now when i start shiretoko, i can see:
```
IcedTea Java Web Browser Plugin

    File name: IcedTeaPlugin.so
    The IcedTea Java Web Browser Plugin 1.4.1 (6b14-1.4.1-0ubuntu12) executes Java applets.
```

yet, when i go to start a java applet, firefox-3.5 spikes the cpu to 100% for several minutes, doesn't load the applet, then the cpu calms down.

so can you help me get the icedtea plugin working?

thanks

---

