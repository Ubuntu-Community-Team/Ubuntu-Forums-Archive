---
title: "Laptop lid behaviour problem"
date: 2011-06-01
forum: General Help
---

### Post by Will777 on 2011-06-01
Hi all,

I'm a first time poster so please excuse me if this is the wrong forum.

Recently installed Ubuntu 11.04 on a HP 8410w laptop. I had previously been running openSuse 11.4.

Everything seems fine - my only problem being that Ubuntu is ignoring the setting in Power Management to hibernate when I close the lid. 

Hibernation works fine when I manually choose the option - it's just the lid behaviour that's not working.

Has anyone come accross this before? I had previously run Ubuntu 10.10 where this was working?

Thanks in advance!

---

### Post by cespinal on 2011-06-01
> **Will777 said:**
> Hi all,

I'm a first time poster so please excuse me if this is the wrong forum.

Recently installed Ubuntu 11.04 on a HP 8410w laptop. I had previously been running openSuse 11.4.

Everything seems fine - my only problem being that Ubuntu is ignoring the setting in Power Management to hibernate when I close the lid. 

Hibernation works fine when I manually choose the option - it's just the lid behaviour that's not working.

Has anyone come accross this before? I had previously run Ubuntu 10.10 where this was working?

Thanks in advance!

Funny.. I have the same problem in Kubuntu. I ask the system to NOT suspend when I close de lid on AC power. It sleeps away anyway.... 

In KDE you are able to override the WHOLE set of laptop lid behaviours so that is how I got to solve my little issue... 

Have you tried using suspend instead of hibernate? I always found that hibernate just takes tooo long...

---

### Post by Will777 on 2011-06-01
> **cespinal said:**
> 
Have you tried using suspend instead of hibernate? I always found that hibernate just takes tooo long...

I tried this:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/701470](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/701470)

I just tried using suspend, not working. But, when I changed the setting back to hibernate it seems to be working now.

It does seem that there are some issues regarding the behaviour settings in Power Management.

---

### Post by coldraven on 2011-06-01
I'm not sure this applies to 11.04, there definitely was a bug in 10.10. It did not seem to store the selected setting correctly.
Check the power settings with gconf-editor, Under apps>gnome-power-manager.
see the screenshot

---

### Post by Will777 on 2011-06-01
coldraven:

Thanks. I did as you suggested and I can see that the settings are being saved correctly.

The hibernation on lid close does work now, but SLOW :( When I hibernate out of Unity it's very quick.

Just wanted to add:
I was a bit hesitant when I first installed Natty - Unity was a bit different, but now that I am used to it I LOVE it and prefer it over Gnome 3.0 - great job!

---

