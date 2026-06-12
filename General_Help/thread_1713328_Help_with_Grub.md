---
title: "Help with Grub"
date: 2011-03-23
forum: General Help
---

### Post by cesarbustios on 2011-03-23
My first post... Hi everyone, I removed my Windows 7 partition and resized with Gparted the Ubuntu partition in order to have the whole disk space. My question is: is it necessary to keep grub for chosing different linux images? :confused: Can i remove/uninstall grub so it can automatically load the newest linux image or do i need to manually remove older linux images? :confused:

Thanks a lot!

Cesar B.

P.D. I'm still working on my english, sorry.

---

### Post by kiyop on 2011-03-23
If you want grub to find all the kernels ("linux images" as you say?), click
"Application" -> "Accessory" -> "Terminal"
and type
```
sudo update-grub
```and enter your password.

Please refer to[[SIZE=1][COLOR=MAROON] The Grub 2 Guide[/COLOR][/SIZE]]("http://ubuntuforums.org/showthread.php?t=1195275")

If you want to delete old unnecessary linux kernels, you can delete them from Synaptic package manager.
Click
"System" -> "Administration" -> "Synaptic..."
and find the packages whose names are:
"linux-headers-2.6."+ OLD VERSION NUMBERS
"linux-image-2.6."+ OLD VERSION NUMBERS

Be careful! Do not delete a current necessary kernel.

<<Edited at 3/24 at 22:42 in JAPAN>>

Thanks wojox and oldfred. I am studying English, too.

---

### Post by cesarbustios on 2011-03-24
Thanks but, in fact, i don't want grub to find anything i just want Ubuntu to load newest kernel... is grub necessary if i don't have dual boot (Windows 7/Ubuntu 10.04)?

I will try your second advice anyway :). Thanks again

---

### Post by wojox on 2011-03-24
It's very necessary. GRand Unified Bootloader. Leave it alone and ubuntu will update to the newest kernel every kernel upgrade.

---

### Post by oldfred on 2011-03-24
You have to have grub, just like windows has a boot loader in the MBR. But if grub only finds one system it will not show the menu, but just boot. After the sudo update-grub it will only find Ubuntu and should not give you menu.

If you want the menu, you then have to hold down the shift key from BIOS until menu appears. You may need menu to boot older kernel if you have trouble with a new kernel, to test memory or to run recovery version.

---

### Post by cesarbustios on 2011-03-24
Thank you for the information! Changing timeout to 0 from grub.cfg will load the newest kernel without showing the menu list right? (Last question i swear!)

---

### Post by cesarbustios on 2011-03-24
> **oldfred said:**
> You have to have grub, just like windows has a boot loader in the MBR. But if grub only finds one system it will not show the menu, but just boot. After the sudo update-grub it will only find Ubuntu and should not give you menu.

If you want the menu, you then have to hold down the shift key from BIOS until menu appears. You may need menu to boot older kernel if you have trouble with a new kernel, to test memory or to run recovery version.

Thanks thats exactly what i want!

---

### Post by magodiafano on 2011-03-27
> **wojox said:**
> It's very necessary. GRand Unified Bootloader. Leave it alone and ubuntu will update to the newest kernel every kernel upgrade.

I am using GRand Unified Bootloader but it does not update to the newest kernel every kernel update. What do I have to do?
I don't like that my grab is full of useless entries...

---

### Post by oldfred on 2011-03-27
See kiyop's post #2 on removing kernels and updating grub's menu.

You may want to check what kernel you are actually running:
Check current kernel:
lsb_release -a

Some new gui tools to modify settings:
HOWTO: Remove Older Kernels via GUI Tweak
[http://ubuntuforums.org/showthread.php?t=1587462](http://ubuntuforums.org/showthread.php?t=1587462)
HOWTO: Grub Customizer 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

It is possible to delete the kernel you are running. When you shutdown it completes the delete & then you cannot reboot.

---

### Post by domu on 2011-03-28
To get grub2 to remember the last kernel choice you made at boot time you may need to change its settings. I have a script which does this at [http://www.timedicer.co.uk](http://www.timedicer.co.uk) under 'My Programs' - look for fix-grub2.sh. Run it from a terminal window thus:```
sudo /bin/bash fix-grub2.sh
```All it does is make sure that these lines appear in /etc/default/grub:```
GRUB_DEFAULT=saved
GRUB_SAVEDEFAULT=true
```

So the next time you boot, your choice of boot environment is remembered and used by default the following time (unless you make a different choice before the timeout expires).

There is also a script there to remove old kernels from disk and from grub (remove-kernel), but maybe you got that sorted already...

---

### Post by kiyop on 2011-03-28
To check version of the kernel currently used,
```
uname -r
```You can check all existing kernels by
```
ls /boot/vml*
```

---

### Post by magodiafano on 2011-03-28
your command does not work! I downloaded the program from your website, then I put it in the /bin/bash folder... using the command in the terminal it does not work. It says "command not found"..

---

