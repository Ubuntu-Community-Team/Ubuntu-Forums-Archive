---
title: "Firefox Problem"
date: 2009-07-02
forum: General Help
---

### Post by Jonathan 916 on 2009-07-02
I just switched to Ubuntu (9.04) and am new to Linux.  When I use Firefox I am unable to get the necessary content from the following site:

[http://www.frontline-connect.com/programs-info.cfm?fac=skatetownroseville&facid=1&levelid=0&seasonid=0&dateid=0&programid=8&uid=0](http://www.frontline-connect.com/programs-info.cfm?fac=skatetownroseville&facid=1&levelid=0&seasonid=0&dateid=0&programid=8&uid=0)

I'm not sure if I need a plugin for Firefox or what the problem is.  Any help would be much appreciated.

---

### Post by abhi_69 on 2009-07-02
may be u need flash-plugins to visit this site & any other sites & get content. u will also need other plugins to play other media in firefox. 1st enable medibuntu repository. guidelines are here-
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
then, type in terminal-
**$ sudo apt-get install flashplugins-nonfree**
to get adobe-flash-plugin.
for other media format, just type the following in terminal-
**$ sudo apt-get install ubuntu-restricted-extras**
thats all!
after this, u can get any content from web & also play various media format using totem/rythmbox.
hope this will help u.........

---

### Post by lovinglinux on 2009-07-02
I can't access that site right now, because I'm experiencing DNS issues, but I think you might have conflicting plugins (very common).

To remove conflicting flash plug-ins and install only the one from Adobe Open "Applications >> Accessories >> Terminal", then paste (CTRL+SHIFT+V) the code below in the terminal window and hit enter:

```
sudo apt-get remove swfdec-mozilla mozilla-plugin-gnash && sudo apt-get install flashplugin-nonfree 
```

Recommended tutorials:

[Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567)
[Comprehensive Multimedia & Video Howto Multimedia & Video](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by sdowney717 on 2009-07-02
it works here, you can also ditch the old firefox and run firefox version 3.5

you will have to install it
command to start is firefox-3.5

---

