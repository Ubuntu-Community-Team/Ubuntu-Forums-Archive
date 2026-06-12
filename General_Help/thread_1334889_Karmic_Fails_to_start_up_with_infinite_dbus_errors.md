---
title: "Karmic Fails to start up with infinite dbus errors"
date: 2009-11-22
forum: General Help
---

### Post by dshookowsky on 2009-11-22
Each time I try to start karmic koala from grub, I get through a graphic with the Ubuntu logo, then back to text mode with infinitely repeating messages all containing:

> 
process %n: arguments to dbus_pending_call_set_notify() were incorrect assertion "pending != null" failed in file dbus-pending-call.c line 596
This is normally a bug in some application using the dbus library.



Does anyone have any tips on what this message means and how I can get back to a working state?  I can mount the drives in an older ubuntu 8.10 cd, but I can't boot from the hard drive

---

### Post by glawas on 2009-12-15
I am experiencing the exact same problem.  After some random update, the system first would only boot to a half wall of text where it was doing checks.  The last check was a battery check.  the last line of that said "...good."

then nothing.  a blinking cursor.  no command line.  typing would produce random characters on the screen and only ctrl+alt+delete seem to do anything.  

If you ctl+alt+delete it would go through a shut down process similar the the boot up process.  a half-wall of text going through some shutdown checks.

after that it would reboot and grub would load again.  So a few times of that and then it just quit all together.  The boot process took a really really long time mostly on a blinking cursor, no text.  Then the repeat dbus error at line 596.

I just gave up and booted into another kernal on the list.  This one got me into ubuntu gui but froze on a white screen with only the top menu bar being distinct.  it has no icons or text on it.

I'm just short of a complete install.  Any ideas?

---

### Post by Tiede on 2010-01-16
Hmmm... It seems we are all getting this error thing...
Did it ever get better for you?

Even a blogger has [an instance of it]("http://johnlawrenceaspden.blogspot.com/2009/11/installing-ubuntu-910-netbook-remix-on.html"), although he somehow got past it later....

I am opening a launchpad bug on this...
Done did it: [bug #508327]("https://bugs.launchpad.net/netbook-remix/+bug/508327") opened on launchpad!

---

### Post by Drunken on 2010-01-23
I am also getting this bug from my flash drive install. Very annoying, I remember installing XBMC and LIRC and a USB WiFi card some time before that reboot, but I am definably sure I didn't preform any system updates - unless XBMC did one without me knowing through one of its dependencies.

I found this, looks like they are aware of it and it is actually a bug with Karmic [https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/477116]("https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/477116")

Let us know if you find any workarounds...

---

### Post by GrGeorgios on 2011-01-17
Hi All
 
Any ideas on this?
Can someone help me?
I have on my Linux box installed a Raid5 with all my files (personal documents etc) and I restarted the box for adding a HDD and now I am not able to boot the system, with this error.
 
Any walkaround? 
 
Thanks for your time!

---

