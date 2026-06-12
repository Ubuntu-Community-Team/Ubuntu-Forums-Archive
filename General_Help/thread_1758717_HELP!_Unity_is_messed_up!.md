---
title: "HELP! Unity is messed up!"
date: 2011-05-15
forum: General Help
---

### Post by jackbones10 on 2011-05-15
I recently got Ubuntu, I'm new to it. I downloaded CompizConfig SettingsManager and all I did was check 1 or 2 items about the way the windows would wiggle or fade and stuff and next thing I now Unity is gone. When I log in through it, nothing is shown but the wallpaper. I researched a little and stumbled accros the following:

[http://ubuntuforums.org/showthread.php?p=10733905](http://ubuntuforums.org/showthread.php?p=10733905)
gconftool --recursive-unset /apps/compiz-1 
gconftool --recursive-unset /apps/compizconfig-1 
The commands have no effect at all.

I also tried: 

unity --reset  and got this

user@user-eME528:~$ unity --reset
Traceback (most recent call last):
  File "/usr/bin/unity", line 198, in <module>
    reset_unity_compiz_profile ()
  File "/usr/bin/unity", line 83, in reset_unity_compiz_profile
    if current_profile_gconfvalue.get_string() == 'unity':
AttributeError: 'str' object has no attribute 'get_string'

Can anyone help me? Is there a way to Re-Install Ubuntu 11.04 from within Single-Boot Ubuntu 11.04?

---

### Post by 5149.5 on 2011-05-15
Try this: Alt+F2. Then enter: ```
unity --reset
``` You won't see anything so type carefully. Then cross your fingers and press enter. If you get lucky, you will get a desktop after a few seconds.

---

### Post by jackbones10 on 2011-05-15
I found a way to get some stuff back in Unity through "Ubuntu (SafeMode) so I opened terminal and also tried commands and yet nothing... Is there a way to re-install Ubuntu 11.04?

---

### Post by 5149.5 on 2011-05-15
> **jackbones10 said:**
> I found a way to get some stuff back in Unity through "Ubuntu (SafeMode) so I opened terminal and also tried commands and yet nothing... Is there a way to re-install Ubuntu 11.04?

Did you try what I suggested?

---

### Post by jackbones10 on 2011-05-15
Tried it just now, not results. Is there any way I can re-install Ubuntu?

---

### Post by 5149.5 on 2011-05-15
> **jackbones10 said:**
> Tried it just now, not results. Is there any way I can re-install Ubuntu?

Put CD in tray, turn on computer, answer questions????

---

### Post by Hedgehog1 on 2011-05-15
To reinstall Ubuntu or refresh your Natty install:

When you boot from the 11.04 LiveCD/LiveUSB, you may have an upgrade path offered in the 'install 11.04'.

[IMG]http://img848.imageshack.us/img848/874/upgradetonatty.png[/IMG]

**If this is not offered**, if you have your data in a separate '/home' partition you can reinstall 11.04 over your 10.10 '/' partition and be sure to not format the '/home' partition:

First, define your '/' (root) partition:

[IMG]http://img31.imageshack.us/img31/7520/04allocdrivespace2.png[/IMG]

[IMG]http://img130.imageshack.us/img130/9673/05allocdrivespace3.png[/IMG]

Then define your '/home' partition:

**[SIZE="4"]IF YOU ARE DOING AN UPGRADE, DO NOT FORMAT THIS PARTITION![/SIZE]**

[IMG]http://img202.imageshack.us/img202/6828/07allocdrivespace5.png[/IMG]

This separates your documents and 'stuff' from the system files and 'stuff' in the '/' partition.

***The Hedge***

:KS

p.s. To learn how to move your '/home' into it's own partition: **_[SeparateHomePartition]("http://www.psychocats.net/ubuntu/separatehome")_**

---

