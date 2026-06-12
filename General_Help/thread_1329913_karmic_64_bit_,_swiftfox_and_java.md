---
title: "karmic 64 bit , swiftfox and java"
date: 2009-11-17
forum: General Help
---

### Post by bowens44 on 2009-11-17
Can anyone tell me how to get java working in swiftfox on karmic ubuntu 64 bit? I have googled but haven't found an answer.

Thanks

---

### Post by fluffman86 on 2009-11-17
Installing it for firefox should automatically work with swiftfox.  Do:

sudo apt-get install flashplugin-nonfree

And see if that works in firefox.  If it works in firefox but not swiftfox, try swiftweasel instead, maybe.  I know it worked for me in swiftweasel.

---

### Post by mikilion on 2009-11-20
I confirm also on Karmic 32 bit Java plugin isn't detect by Swiftfox 3.5.5.

---

### Post by mikilion on 2010-02-08
I solved as described here:
[Java plugin not showing up (on Ubuntu Karmic)](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Java_plugin_not_showing_up_.28on_Ubuntu_Karmic.29)

If the Java plugin is not showing up, this is due to a [bug in sun-java6-plugin package](https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/509727) on Ubuntu Karmic. To fix this, follow these steps:

1. Make sure package sun-java6-plugin is installed, by running this command:
```
sudo apt-get install sun-java6-plugin
```
2. Run the following command to create the missing link (copy and paste the entire line into a terminal, and press enter):
```
sudo update-alternatives --install /usr/lib/mozilla/plugins/libjavaplugin.so mozilla-javaplugin.so /usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so 50
```
This will place the appropriate link to the java plugin into /usr/lib/mozilla/plugins.

---

