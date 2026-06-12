---
title: "firefox is slow"
date: 2010-09-23
forum: General Help
---

### Post by termin on 2010-09-23
when i get rid of the navagation and bookmarks bars then it loads pages faster for some reason. i tried it with and without those bars, and without it its faster. yes i emptied my cache and history and cookies when i did it both times. anyway, why is this?

---

### Post by lovinglinux on 2010-09-24
Probably because your bookmarks database is full of left-overs and needs to be optimized. See [http://firefox-tutorials.blogspot.com/2010/05/database-optimization.html](http://firefox-tutorials.blogspot.com/2010/05/database-optimization.html)

---

### Post by donut123 on 2010-09-28
> **lovinglinux said:**
> Probably because your bookmarks database is full of left-overs and needs to be optimized. See [http://firefox-tutorials.blogspot.com/2010/05/database-optimization.html](http://firefox-tutorials.blogspot.com/2010/05/database-optimization.html)
Hello....first open Firefox extentions.

Have you tried :

UN Install the Ubuntu firefox modifications from the add ons of firefox, was a suggestion followed with reboot.
By default Firefox puts its cache in your home partition.You can speed   up Firefox and reduce disk writes by moving this cache into RAM if you   have 1GB RAM or more.

1.Edit /etc/fstab,open terminal from Applications->Accessories menu and type:

    Code:sudo gedit /etc/fstab



Add following into this file and close it.

    tmpfs /tmp tmpfs noexec,defaults,noatime 0 0
    tmpfs /var/tmp tmpfs noexec,defaults,noatime 0 0

2.Edit /etc/sysctl.conf:

   Code: sudo gedit /etc/sysctl.conf



add this line and save it:

    vm.swappiness=1

3.
Type  about:config in firefox address bar and click I'll be  careful,I  promise!.Right click on blank area and create a new string  value called  browser.cache.disk.parent_directory,set its value to /tmp

Now,reboot your system and experience the performance. [IMG]http://www.ultimateeditionoz.com/forum/images/smilies/grin.png[/IMG]

---

### Post by donut123 on 2010-09-28
Here is  a link to Firefox...
[http://support.mozilla.com/en-US/search?locale=en-US&q=firefox+is+slow&sa=](http://support.mozilla.com/en-US/search?locale=en-US&q=firefox+is+slow&sa=)
[CENTER][COLOR=Purple]-Version- GheTTo

Kernel    : Linux 2.6.31-20-generic (x86_64) 


Default C Compiler    : GNU C Compiler version 4.4.1 (Ubuntu 4.4.1-4ubuntu9) 
Distribution        :Ultimate Edition Ubuntu
Desktop Environment        : GNOME 2.28.1 [/COLOR][CENTER][COLOR=#0040ff]

Ultimate Edition [/COLOR]
Wow I thought something was missing. 
I didnt need all that anyway. Thanks buddy !
[URL="http://my.opera.com/Donut123/blog/"]
[/URL][/CENTER]
[/CENTER]

---

### Post by lovinglinux on 2010-09-28
> **donut123 said:**
> Hello....first open Firefox extentions.

Have you tried :

UN Install the Ubuntu firefox modifications from the add ons of firefox, was a suggestion followed with reboot.
By default Firefox puts its cache in your home partition.You can speed   up Firefox and reduce disk writes by moving this cache into RAM if you   have 1GB RAM or more.

1.Edit /etc/fstab,open terminal from Applications->Accessories menu and type:

    Code:sudo gedit /etc/fstab



Add following into this file and close it.

    tmpfs /tmp tmpfs noexec,defaults,noatime 0 0
    tmpfs /var/tmp tmpfs noexec,defaults,noatime 0 0

2.Edit /etc/sysctl.conf:

   Code: sudo gedit /etc/sysctl.conf



add this line and save it:

    vm.swappiness=1

3.
Type  about:config in firefox address bar and click I'll be  careful,I  promise!.Right click on blank area and create a new string  value called  browser.cache.disk.parent_directory,set its value to /tmp

Now,reboot your system and experience the performance. [IMG]http://www.ultimateeditionoz.com/forum/images/smilies/grin.png[/IMG]

Is a lot simpler if you do this [http://firefox-tutorials.blogspot.com/2010/08/use-ramdisk-to-save-firefox-cache.html](http://firefox-tutorials.blogspot.com/2010/08/use-ramdisk-to-save-firefox-cache.html)

---

### Post by donut123 on 2010-09-28
> **lovinglinux said:**
> Is a lot simpler if you do this [http://firefox-tutorials.blogspot.com/2010/08/use-ramdisk-to-save-firefox-cache.html](http://firefox-tutorials.blogspot.com/2010/08/use-ramdisk-to-save-firefox-cache.html)
aha...I was trying to help another dude. I guess he will be comming on over..Thank you

---

