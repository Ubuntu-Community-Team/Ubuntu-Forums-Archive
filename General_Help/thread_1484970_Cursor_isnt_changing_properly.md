---
title: "Cursor isnt changing properly"
date: 2010-05-16
forum: General Help
---

### Post by musdem on 2010-05-16
Whenever I change themes to the azenis theme in ubuntu 10.04 the cursor will not change themes properly for example it will change to the proper cursor when I hover over a close button (I'm using emerald themes too) when hovering in certain programs (like firefox) and when moving icons. I have tried to change the theme to another one reboot to hopefully "reset" the mouse then change back but it didn't work. I'm using ubuntu 10.04 64 bit.

---

### Post by NeverHide on 2010-05-19
i have the same problem and tried to use this 'fix' [http://ubuntuforums.org/showthread.php?t=1483366](http://ubuntuforums.org/showthread.php?t=1483366) but ended up with the same thing,the only difference is that instead of the white,i get the default black cursor this time

---

### Post by musdem on 2010-05-29
wow now i have the same problem do you know of a way to change it back to the white one at least? because the black theme looks even worse than the white one.

---

### Post by 2hot6ft2 on 2010-05-30
The cursor issue is know and as far as I know is still not being worked on by ubuntu since they consider it cosmetic and of low importance.

TheeMahn, known here as TheeMahn2003, has been kind enough to create a fix for it for Ultimate Edition. Since he is a firm believer in open source and helping people here is the fix.

Check what version of compiz you have installed by searching for "compiz" in
System > Administration > Synaptic Package Manager
Download the appropriate package and double click on it.
It should say same version already installed.
Click on reinstall.
When it finishes logout and back in (no need to reboot just log out and back in).
Works great for me with Windows Manager set to Compiz and Windows Decorator set to GTK.
No more big ugly black cursor.
Enjoy

[x86 compiz version 0.8.4]("http://rapidshare.com/files/393136266/compiz-core_0.8.4-0ubuntu15_i386.deb.html")
MD5: EB4FF7F41FF5AB1FE5FE1720C29F51A2

[x64 compiz version 0.8.6]("http://rapidshare.com/files/393137143/compiz-core_0.8.6-0ubuntu1_ppa1_amd64.deb.html")
MD5: BD74BB2E85BEE9BFE7CA7ACD6CD2C071

An additional thanks to bpollen for compiling the 0.8.6 x64 version.
You're mileage may vary but the debs. are working great for myself and others.
:guitar:

---

### Post by musdem on 2010-05-30
OK so i installed the compiz version 0.8.4 and now i cant get back onto ubuntu all that happens is when i boot up it stays on the dark purple ubuntu load screen and wont move past that it boots into ubuntu properly if i go into recovery mode and then graphical failsafe mode. any ideas on how to fix this?

---

### Post by 2hot6ft2 on 2010-05-30
> **musdem said:**
> OK so i installed the compiz version 0.8.4 and now i cant get back onto ubuntu all that happens is when i boot up it stays on the dark purple ubuntu load screen and wont move past that it boots into ubuntu properly if i go into recovery mode and then graphical failsafe mode. any ideas on how to fix this?
You mean after applying the fix it did that. I don't know why it would do that but boot up into recovery mode since that's how you can get in and either go to Synaptic and search for compiz-core select it and mark it for re-installation and apply.
That will put you back where you were before the fix. Or from the command prompt run
```
sudo aptitude reinstall compiz-core
```
apt-get doesn't have a reinstall option but aptitude does.
:confused:
I'm going to remove that one in that case so it doesn't happen to anyone else.

If you still have problems booting [this seems to fix some of them]("http://ultimateeditionoz.com/forum/viewtopic.php?f=73&t=1066&p=4092#p4092") where the cause is the resolution isn't set properly in the grub setting which has nothing to do with the compiz fix.

---

### Post by musdem on 2010-05-30
Ah ha thank you I can get in now :) but the cursor is still not back to normal :( so I'm still not sure what to do

---

