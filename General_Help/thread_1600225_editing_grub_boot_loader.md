---
title: "editing grub boot loader"
date: 2010-10-18
forum: General Help
---

### Post by Buddha Belly on 2010-10-18
Hello, 

I've noticed that after upgrading a couple distro's of Linux, my boot loader is quite long and I'm trying to get it cleaned up.  Now I've tried a couple option like vi /boot/grub/menu.lst and other variants of this command, but when in the edit mode, there isn't anything listed.  Does anyone know what I might be doing wrong?

Thanks

---

### Post by garner_nc on 2010-10-18
Grub has changed. You probably didn't notice but Ubuntu is now using Grub 2 (1.98). I had a heck of a time trying to get things the way I wanted them using the recommended methods. It's a complicated bunch of hooey now.

There is no longer a menu.lst file. It's become menu.cfg or grub.cfg I believe. When you open it it says not to edit it but it's the easiest way to get things the way you want them. After you edit it make a copy of it, something like menu.cfg.bak. Reason for the copy is when you update your kernel. It triggers Grub 2 to re-run its configuration process again so you get the same mess back. When you do, you just copy your backup to menu.cfg and add the new kernel info. Then make another backup.

You can probably tell I was REALLY irritated by the Grub 2 changes. Grub was a beautiful model of simplicity. Now it's an over complex Rube Goldberg affair.

There are instructions around on how to remove Grub 2 and revert to Grub 1. It's on my list but I haven't had time.

All the Best,
D. White

---

### Post by Buddha Belly on 2010-10-18
Oh man that does sound like more work than I had anticipated.  I might do like you said and just downgrade to version 1.  Thanks for the help, I appreciate it.

---

### Post by oregonbob on 2010-10-18
> **garner_nc said:**
> Grub has changed. .... It's a complicated bunch of hooey now.

LOL, I agree totally. Grub used to be quite simple - just edit menu.lst. Now it seems as if a programmer was too bored and made it complicated so most people can't even change it! I had exact same experience.

Each new version of software should get easier to use, not more difficult. They sure blew grub2. I'll bet it is fixed in later releases.
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by Quackers on 2010-10-18
Have a look here
[http://ubuntuforums.org/showthread.php?t=1541785&highlight=deleting+grub+menu+items](http://ubuntuforums.org/showthread.php?t=1541785&highlight=deleting+grub+menu+items)

---

### Post by oldfred on 2010-10-18
Keep at least one older kernel in case of issues, but you can delete the older kernels:

In synaptic search for linux-image to choose to delete old ones
More info in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

A Very Easy Alternate GUI Method - Ubuntu-Tweak
[http://ubuntuforums.org/showthread.php?t=818177](http://ubuntuforums.org/showthread.php?t=818177)
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

You can create a custom menu just by copying other systems into 40_custom and editing just like in old grub's menu.lst.

I used drs305's command to limit ubuntu entries to two, turned off os_prober so it does not look for other systems and totally customized my 40_custom.
Copy the windows entries from this:
gedit /boot/grub/grub.cfg
Copy them to and edit :
gksudo gedit /etc/grub.d/40_custom

includes line to limit display to two
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)

I added this to turn off prober :
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or
sudo chmod a-x /etc/grub.d/30_os-prober

---

