---
title: "Boot windows first."
date: 2010-06-19
forum: General Help
---

### Post by Terry19 on 2010-06-19
Gday, 
I use ubuntu as a backup tool, and it has saved me a few times. But i normally use windows. I would like to disable the GRUB screen that comes up giving me the option of OS. I would like windows to boot first and not have the screen, maybe a button that i depress at start up that can boot ubuntu or something like that. I also want to be able to test HDD's without GRUB load failed Error 17 coming up... any support would be greatly appreciated. 
[email]terryk_tv@hotmail.com[/email]

---

### Post by dcstar on 2010-06-19
> **Terry19 said:**
> Gday, 
I use ubuntu as a backup tool, and it has saved me a few times. But i normally use windows. I would like to disable the GRUB screen that comes up giving me the option of OS. I would like windows to boot first and not have the screen, maybe a button that i depress at start up that can boot ubuntu or something like that. I also want to be able to test HDD's without GRUB load failed Error 17 coming up... any support would be greatly appreciated. 
[email]terryk_tv@hotmail.com[/email]

Look at the Grub2 HOWTOs, they spell out how to preset the selection.

---

### Post by Terry19 on 2010-06-19
where abouts is Grub2 howto's? is it in these forums?

---

### Post by Terry19 on 2010-06-19
> **dcstar said:**
> Look at the Grub2 HOWTOs, they spell out how to preset the selection.
I had a look, it didnt help at all. is there a simpler way. I might end up having to remove the linux hdd, but then again i cant because error 17 comes up.

---

### Post by nemiux on 2010-06-19
You can remove grub by using a program ms-sys, but i don't know what you should enter in boot.ini to boot ubuntu

---

### Post by wilee-nilee on 2010-06-19
dcstar is correct to the link to edit, but what your asking for, ie disabling the grub screen is not a good idea. You can change the order so that MS is the default boot and lower the time out. I wouldn't go below three seconds though as you never know when you might need the Ubuntu programs. A user a couple of weeks ago set the time out to 0 and couldn't ever get back in.

Grub is easier to manipulate and control then any 3rd party like easybcd or the MS bootloader.

I use startup manager in synaptic in Ubuntu to change the boot default and timer, but if you get a kernel update it will default to the line it was set at rather then the new kernel or MS. So this is the easiest way to set the default boot, and time out, but you just have to go back and reset the default on a Ubuntu kernel update.

As far as testing HD's grub is on the HD your using if you take it out the bootloader in the mbr of any HD inserted is the bootloader.

So here are two links 
[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)
[https://help.ubuntu.com/community/Grub2#Upgrading](https://help.ubuntu.com/community/Grub2#Upgrading)

---

