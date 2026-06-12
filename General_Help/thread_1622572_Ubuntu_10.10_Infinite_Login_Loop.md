---
title: "Ubuntu 10.10 Infinite Login Loop"
date: 2010-11-15
forum: General Help
---

### Post by jodanlime on 2010-11-15
So, this morning my Ubuntu machine was working perfectly, but when I turned the computer back on in the afternoon it didn't load the desktop completely, instead it brought me to the login page (I wanted auto log on and it was working). When I try to login the computer reverts to the login page, like a loop. I can, however, login if I use the safe mode desktop session. I didn't install any software lately, and I updated my system a few days ago. Any help would be greatly appreciated.
I'm using Ubuntu 10.10 on a Dell Inspiron 2500

jodanlime

---

### Post by yuki-nagato on 2010-11-16
> **jodanlime said:**
> I can, however, login if I use the safe mode desktop session.
xorg is probably not configured properly.  you can reconfigure xorg
by hitting esc at the screen listing the kernels that you have and select
the recovery option.  this brings you to a screen giving you a few options.
you want to choose the xorg option and have it reconfigure its self.

---

### Post by tbar3 on 2010-11-26
I have the same issue, but am not seeing any recover options. Am i missing something?

This is getting kind of frustrating -- i'm about ready to download and install 10.4 instead...

---

### Post by polarbear10 on 2010-12-14
> **jodanlime said:**
> So, this morning my Ubuntu machine was working perfectly, but when I turned the computer back on in the afternoon it didn't load the desktop completely, instead it brought me to the login page (I wanted auto log on and it was working). When I try to login the computer reverts to the login page, like a loop. I can, however, login if I use the safe mode desktop session. I didn't install any software lately, and I updated my system a few days ago. Any help would be greatly appreciated.
I'm using Ubuntu 10.10 on a Dell Inspiron 2500

jodanlime

I too have been very frustrated by this issue but hey, it's super old hardware!

Ok so I think I figured a way around but I had to use a second machine to do it.

First, as soon as your inspiron boots up hit the Esc key when you hear the cd rom drive spin up for the first time to get to the grub boot menu.  Boot up into root with networking and install ssh

sudo apt-get install ssh

then head over to this site on your other computer and save the contents of the xorg.conf file to a file on your desktop as a plain txt file.

[http://threeeighthsspacer.com/blog/2009/09/08/dell-inspiron-2500-with-intel-82815-graphics-xorgconf-for-1024x768/](http://threeeighthsspacer.com/blog/2009/09/08/dell-inspiron-2500-with-intel-82815-graphics-xorgconf-for-1024x768/)

then back on your inspiron get the ip address by using ifconfig and scp the xorg.conf file from your computer to the inspiron.  Put it in the right spot - /etc/X11/ and that's it.  Reboot and you're done.

I must have made a type when I tried to type the file out by hand so I had to scp a copy over in the end...  Before anyone asks why go to all this trouble - Failsafe video didn't work for me...

I'm too tired right now to be happy I figured it out but hopefully this helps those of you who are beating your head against the wall ;)

Cheers,

PolarBear10

---

