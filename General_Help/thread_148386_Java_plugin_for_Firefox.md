---
title: "Java plugin for Firefox"
date: 2006-03-22
forum: General Help
---

### Post by Shoriminimoe on 2006-03-22
I've repeatedly tried to install Java but everytime it won't work. I've used Automatix but still I can't use java applets in my browser. Can anyone help me out?

---

### Post by joshuapurcell on 2006-03-22
Has the java plugin ever worked in any browser for you? Which browser (and version) are you using now? If you navigate to the **about: plugins** page (if you are using Firefox), what is listed under the Java plug-in section? Here's a printout of what's listed for me:```
Java(TM) Plug-in 1.5.0_05-b05

    File name: libjavaplugin_oji.so
    Java(TM) Plug-in 1.5.0_05

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	Java 		Yes
application/x-java-applet 	Java 		Yes
application/x-java-applet;version=1.1 	Java 		Yes
application/x-java-applet;version=1.1.1 	Java 		Yes
application/x-java-applet;version=1.1.2 	Java 		Yes
application/x-java-applet;version=1.1.3 	Java 		Yes
application/x-java-applet;version=1.2 	Java 		Yes
application/x-java-applet;version=1.2.1 	Java 		Yes
application/x-java-applet;version=1.2.2 	Java 		Yes
application/x-java-applet;version=1.3 	Java 		Yes
application/x-java-applet;version=1.3.1 	Java 		Yes
application/x-java-applet;version=1.4 	Java 		Yes
application/x-java-applet;version=1.4.1 	Java 		Yes
application/x-java-applet;version=1.4.2 	Java 		Yes
application/x-java-applet;version=1.5 	Java 		Yes
application/x-java-applet;jpi-version=1.5.0_05 	Java 		Yes
application/x-java-bean 	Java 		Yes
application/x-java-bean;version=1.1 	Java 		Yes
application/x-java-bean;version=1.1.1 	Java 		Yes
application/x-java-bean;version=1.1.2 	Java 		Yes
application/x-java-bean;version=1.1.3 	Java 		Yes
application/x-java-bean;version=1.2 	Java 		Yes
application/x-java-bean;version=1.2.1 	Java 		Yes
application/x-java-bean;version=1.2.2 	Java 		Yes
application/x-java-bean;version=1.3 	Java 		Yes
application/x-java-bean;version=1.3.1 	Java 		Yes
application/x-java-bean;version=1.4 	Java 		Yes
application/x-java-bean;version=1.4.1 	Java 		Yes
application/x-java-bean;version=1.4.2 	Java 		Yes
application/x-java-bean;version=1.5 	Java 		Yes
application/x-java-bean;jpi-version=1.5.0_05 	Java 		Yes
```

---

### Post by harisund on 2006-03-22
[http://plugindoc.mozdev.org/faqs/firefox-linux.html#install-java](http://plugindoc.mozdev.org/faqs/firefox-linux.html#install-java)

---

### Post by KansasJoe on 2006-03-22
Download it here [http://www.java.com/en/download/linux_manual.jsp](http://www.java.com/en/download/linux_manual.jsp)

Follow instructions here [http://www.java.com/en/download/help/5000010500.xml#selfextracting](http://www.java.com/en/download/help/5000010500.xml#selfextracting)

i suggest extracting the file to home directory to avoid permission issues and your plugin for mozilla is located in /home/"your username"/.mozilla/plugins 

so now when you go to set up the link you will open terminal and
cd .mozilla/plugins

next in terminal type

ln -s /home/"your username"/jre1.5.0/plugin/i386/ns7/libjavaplugin_oji.so

you can copy this exactly minus the your username which will obviously be your username and you must extract the jre file you dl to your home folder.

---

### Post by mechanicalmouse on 2006-04-19
Thanks for the tips!

I've installed java runtime on hoary (in /usr/lib) and have set up a link in the mozilla plugins folder, but when I go to about: plugins, still no java. In the mozilla plugins folder I can see:

 -rw-r--r--  1 root root     856 2004-10-06 18:37 flashplayer.xpt
-rw-r--r--  1 root root 2092960 2004-10-06 18:37 libflashplayer.so
-rw-r--r--  1 root root  199840 2005-04-04 15:42 mplayerplug-in.so
lrwxrwxrwx  1 root root      57 2006-04-19 19:27 libjavaplugin_oji.so -> /usr/li b/j2re1.5-sun/plugin/i386/ns7/libjavaplugin_oji.so

Does anyone have any ideas?

Cheers!

---

### Post by mechanicalmouse on 2006-04-20
I tried removing the above link and creating another in the  mozilla-firefox/plugins directory but still no luck

lrwxrwxrwx  1 root root 39 2005-12-11 17:59 mplayerplug-in.so -> ../../mozilla/plugins/mplayerplug-in.so
lrwxrwxrwx  1 root root 39 2006-04-10 17:22 libflashplayer.so -> ../../mozilla/plugins/libflashplayer.so
lrwxrwxrwx  1 root root 37 2006-04-10 17:22 flashplayer.xpt -> ../../mozilla/plugins/flashplayer.xpt
lrwxrwxrwx  1 root root 39 2006-04-11 17:47 libjavaplugin.so -> /etc/alternatives/firefox-javaplugin.so
lrwxrwxrwx  1 root root 57 2006-04-20 18:17 libjavaplugin_oji.so -> /usr/lib/j2re1.5-sun/plugin/i386/ns7/libjavaplugin_oji.so

not sure if I should be posting this in another place as I'm pretty new to this?!

Cheers!

---

### Post by mcmuffy on 2006-04-25
I'm currently searching for an answer to this myself. I'll port it I have any luck.

---

### Post by yomoenco on 2006-04-28
I have the latest firefox installed (1.5.0.2) via Automatix and finally found a */opt/firefox/plugins* directory where I had to create the link (after unsuccessfully  trying /usr/lib/mozilla/plugins and /usr/lib/mozilla-firefox/plugins).
There was a link but it was pointing to a file that does not exist (libjavaplugin_oji.so -> /usr/lib/j2re1.5-sun/plugin/i386/ns7/libjavaplugin_oji.so)
Removed it (**rm /opt/firefox/plugins/libjavaplugin_oji.so**)
and linked it again (**ln -s /usr/java/jre1.5.0_06/plugin/i386/ns7/libjavaplugin_oji.so /opt/firefox/plugins/libjavaplugin_oji.so**)

Now that I know,  I noticed the hint....(in a terminal window type `ps -ef|grep fire` mine showed that firefox was running from /opt/firefox/)
   ps -ef|grep fire
   andre     7772     1  0 22:08 ?        00:00:00 /bin/sh /usr/bin/firefox
   andre     7783  7772  0 22:08 ?        00:00:00 /bin/sh /opt/firefox/run-mozilla.sh /opt/firefox/firefox-bin
   andre     7788  7783  9 22:08 ?        00:00:35 /opt/firefox/firefox-bin
   root      7872  6639  0 22:14 pts/0    00:00:00 grep fire

Hope that helps,
   Andre

---

### Post by akimmell on 2006-04-28
[QUOTE=yomoenco]I have the latest firefox installed (1.5.0.2) via Automatix and finally found a */opt/firefox/plugins* directory where I had to create the link (after unsuccessfully  trying /usr/lib/mozilla/plugins and /usr/lib/mozilla-firefox/plugins).
There was a link but it was pointing to a file that does not exist (libjavaplugin_oji.so -> /usr/lib/j2re1.5-sun/plugin/i386/ns7/libjavaplugin_oji.so)
Removed it (**rm /opt/firefox/plugins/libjavaplugin_oji.so**)
and linked it again (**ln -s /usr/java/jre1.5.0_06/plugin/i386/ns7/libjavaplugin_oji.so /opt/firefox/plugins/libjavaplugin_oji.so**)

Now that I know,  I noticed the hint....(in a terminal window type `ps -ef|grep fire` mine showed that firefox was running from /opt/firefox/)
   ps -ef|grep fire
   andre     7772     1  0 22:08 ?        00:00:00 /bin/sh /usr/bin/firefox
   andre     7783  7772  0 22:08 ?        00:00:00 /bin/sh /opt/firefox/run-mozilla.sh /opt/firefox/firefox-bin
   andre     7788  7783  9 22:08 ?        00:00:35 /opt/firefox/firefox-bin
   root      7872  6639  0 22:14 pts/0    00:00:00 grep fire

Hope that helps,
   Andre[/QUOTE]
Andre.
That solved my problem.
I've been trying for 2 weeks to get jre running.
Downloaded the file many times.  made the ln -s to every directory I could think of (except /opt)  now it's working fine.
Thank  you thank you thank you.  I completely forgot about ps -ef.
Good job.
Andy

---

