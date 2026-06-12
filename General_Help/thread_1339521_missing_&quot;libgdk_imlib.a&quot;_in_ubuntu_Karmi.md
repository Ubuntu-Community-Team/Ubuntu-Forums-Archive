---
title: "missing &quot;libgdk_imlib.a&quot; in ubuntu Karmic Koala"
date: 2009-11-27
forum: General Help
---

### Post by skip2 on 2009-11-27
Ubantu

I am trying to compile CARMEN a robotics software package I have used on previous versions of Ubantu. When I ran ./configure I received the message that  libgdk_imlib.a was missing. 

.....

Searching for GTK... found, version 2.18.3
Searching for libgdk_imlib.a... not found

Could not find libgdk_imlib.a in /usr/lib,
/usr/local/lib, nor in /opt/gnome/lib/
Please install libgdk_imlib.a or
re-run ./configure with --nographics
.....
 I then ran: 

cliff@Linux-laptop:~/carmen-0.7.4-beta/src$ sudo apt-get install libgdk_imlib
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package libgdk_imlib
cliff@Linux-laptop:~/carmen-0.7.4-beta/src$ 

As you see it can not install the lib.
How can I resolve this problem. I can not change the CARMEN applicatioin, it is maintained by Carnegie Mellon University. 


Thanks for your help
Skip2

---

### Post by Virtual Liberty on 2009-11-27
[libimlib2-dev]("http://packages.ubuntu.com/karmic/libimlib2-dev") should solve the problem.

---

### Post by skip2 on 2009-11-27
Thank You for the reply. 
I installed this package as you recommended and the library in question "libgdk_imlib.a" was not contained in this package. I would greatly appreciate any other guidance to obtain this library.

Thanks
Skip2

---

### Post by Virtual Liberty on 2009-11-27
Check [this guide]("http://www.howtoforge.com/apt_file_debian_ubuntu") - all you need is patience.

---

### Post by skip2 on 2009-11-27
Thank You I will keep searching!

---

