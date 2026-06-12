---
title: "Disable touchpad in Karmic"
date: 2009-11-29
forum: General Help
---

### Post by isee on 2009-11-29
Hey All!

In 9.04, I had an option to disable my touchpad altogether.  In 9.10, I can only disable while typing.  This latter option is not sufficient, as my touchpad causes too many problems.

I have done an upgrade, then reinstalled 9.04 clean and now have dual boot with 9.10 on a new partition.

This was a problem for me in the begining, until someone advised me how to turn it off in 9.04.  The upgrade took away the solution, which is kinda a problem for me.  So I cannot upgrade my laptop.  I hope this can be resolved at least by the time they stop supporting 9.04.

---

### Post by cybrsaylr on 2009-11-30
I'm interested in doing this to.
Touchpad is too sensitive on my Toshiba laptop with KK and I use a wireless mouse most of the time. When typing you still touch the touchpad which causes annoying problems.

---

### Post by isee on 2009-11-30
Hello cybrsaylr!

Was your problem with the upgrade also?  In 9.04, you can disable the touchpad completely, whereas in 9.10 you can only select disable while typing.

Trouble with "disable while typing", while it sounds good in theory, it is trying to be too intuitive.  I stop to think while I type, hands hovering over the keyboard, and my touchpad just seems to be too sensitive.

As such, I cannot use 9.10, as I write essays, and cannot have my cursor jumping around, whether I am typing or not.

---

### Post by cybrsaylr on 2009-12-01
Yep I have thee same problem with 9.10, the touchpad just seems to be too sensitive.

---

### Post by sroske on 2009-12-16
this worked for me

[https://bugs.launchpad.net/gnome-control-center/+bug/404638](https://bugs.launchpad.net/gnome-control-center/+bug/404638)


Hasnain Lakhani  wrote on 2009-10-31:  	  #17

Temporary workaround:

sudo apt-get install gpointing-device-settings && sudo gpointing-device-settings

From there, set the touchpad to off. and make sure to keep the System -> Preferences -> Mouse -> Touchpad -> "Disable touchpad while typing" setting off, otherwise the touchpad will just be re-enabled automatically.

That should keep the touchpad disabled.

---

### Post by wojox on 2009-12-16
[http://ubuntuforums.org/showthread.php?p=8274657](http://ubuntuforums.org/showthread.php?p=8274657)

---

### Post by szirakitamas on 2010-01-09
Hi,

the solution of this program for me is [this]("http://ubuntuforums.org/showpost.php?p=8634543&postcount=38").
If originally you do not have an option like this you can create a script for this command and make it possible to run at startup.

---

### Post by smerral on 2010-01-09
My solution is to add 
sudo modprobe -r psmouse  
to etc/init.d/rc.local

Add immediately after #! /bin/sh

Disables touchpad at boot.

---

### Post by isee on 2010-01-31
Thanks much for all the replies!  This is very good information for me.  I'm going to try upgrading again soon.

Thanks again!

---

### Post by sandkernel on 2010-01-31
> **isee said:**
> Thanks much for all the replies!  This is very good information for me.  I'm going to try upgrading again soon.

Thanks again!
I have a T400 - I disabled the touchpad in the BIOS - worked like a charm.

---

### Post by nanonils on 2010-02-27
Luckily that also disables the buttons at the edge of the computer, not just the pad itself (OK, maybe I didn't get that they are considered part of the touchpad). That has been the most annoying part to me when I have my laptop on my lap while reclined and inadvertently click.
Thanks for the fix!

---

### Post by wilee-nilee on 2010-02-27
Hit Fn-F7 this will disable the touchpad in Linux and Windows. Sometimes I have to try it a couple of times to get it to work but it always does.

---

### Post by nanonils on 2010-02-27
Wait! Noooo - both the function key and the gsynaptic app only temporarily disable the darn pad as I'm just realizing. Where is the time out for this function? I'll try bios perhaps as well but the second user of this laptop does like the touchpad and hates the red mini joystick.

---

### Post by cogitordi on 2010-02-28
This works:

= install gsynaptics
= System>Preferences>Touchpad : clear Enable Touchpad
= System>Preferences>Mouse : clear Disable Touchpad while typing

The latter setting is what is reactivating the touchpad.

Tip discovered here:
[https://bugs.launchpad.net/gnome-control-center/+bug/404638/comments/10](https://bugs.launchpad.net/gnome-control-center/+bug/404638/comments/10)

I am using Koala on a Dell Mini 10v. I don't want to disable the touchpad in the BIOS because I may not always have a mouse connected.

---

### Post by nanonils on 2010-03-02
Super! That did the trick for good on my T61 Thinkpad! No bios needed.
Thank you!

---

### Post by CharlieFoxtrot on 2010-03-11
Thank you cogitordi! This did the trick. I've been using gpointing-device-settings for months and had to put up with re-disabling the touchpad on every boot.

---

