---
title: "XMMS Problems..."
date: 2005-03-13
forum: General Help
---

### Post by MicroChris on 2005-03-13
Hey guys,

I'm new to Linux, but not completely new. I ran Slackware 9 and now Im on Ubuntu Warty 4.10 (rockin!  8) )

Anyway, Ive searched and searched for this, and cant find an answer. 

I installed Ubuntu last week, while my Net connection was still down, therefore couldnt upgrade during the install. I added the repositories that I found on the Ubuntu guide, ran apt-get update, apt-get upgrade, and got, "0 Packages Upgraded", blah blah.. So, it seems that every program I try to run runs into some problem, which I later fix somehow.

However, XMMS just wont work. I try "sudo apt-get install xmms" and get:

```
root@ubuntu:/home/chris # apt-get install xmms
Reading Package Lists... Done
Building Dependency Tree... Done
xmms is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
``` 

Ok, cool. Lets try to run it:

```
root@ubuntu:/home/chris # xmms
xmms: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
``` 

I've tried installing lib dev packages, but to no avail.. I need help..


Thanks!
Chris

---

### Post by bored2k on 2005-03-13
[QUOTE=MicroChris]Hey guys,

I'm new to Linux, but not completely new. I ran Slackware 9 and now Im on Ubuntu Warty 4.10 (rockin!  8) )

Anyway, Ive searched and searched for this, and cant find an answer. 

I installed Ubuntu last week, while my Net connection was still down, therefore couldnt upgrade during the install. I added the repositories that I found on the Ubuntu guide, ran apt-get update, apt-get upgrade, and got, "0 Packages Upgraded", blah blah.. So, it seems that every program I try to run runs into some problem, which I later fix somehow.

However, XMMS just wont work. I try "sudo apt-get install xmms" and get:

```
root@ubuntu:/home/chris # apt-get install xmms
Reading Package Lists... Done
Building Dependency Tree... Done
xmms is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
``` 

Ok, cool. Lets try to run it:

```
root@ubuntu:/home/chris # xmms
xmms: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
``` 

I've tried installing lib dev packages, but to no avail.. I need help..


Thanks!
Chris[/QUOTE]
 get beep-media-player

---

### Post by MicroChris on 2005-03-13
Gettin' it now. Thanks man!

---

### Post by bored2k on 2005-03-13
[QUOTE=MicroChris]Gettin' it now. Thanks man![/QUOTE]
 BTW, beep supports XMMS skins and it has mostly every xmms plugin.

Check
[http://www.sosdg.org/~larne/w/Plugin_list](http://www.sosdg.org/~larne/w/Plugin_list)

---

### Post by MicroChris on 2005-03-13
Awesome! I like Beep better than xmms already!

Thanks again for the quick responses and help.

-Chris

---

