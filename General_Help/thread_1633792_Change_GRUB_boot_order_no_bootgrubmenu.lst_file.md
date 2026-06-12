---
title: "Change GRUB boot order: no /boot/grub/menu.lst file"
date: 2010-11-29
forum: General Help
---

### Post by MorrisseyJ on 2010-11-29
Hi i am trying to change the boot order on the GRUB menu so that the countdown automatically starts on an older kernel. 

From what i can see all the solutions on the web want me to edit the /boot/grub/menu.lst file. The problem is that i don't have one. Someone also mentioned that if i don't have a menu.lst file then i should look for the grub.conf file. I don't have on of those either. The closest thing in /boot/grub is grub.cfg but that looks nothing like the descriptions i have heard of /boot/grub/menu.lst file

Can anyone tell me what to do.

Thanks.

---

### Post by WorMzy on 2010-11-29
menu.lst is for grub legacy, grub.cfg is for grub 2.

You might want to read this: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by Christmas on 2010-11-29
Yes, /boot/grub/menu.lst was the file used by the legacy Grub, which is not included in Ubuntu since it uses the newer Grub2. I believe the file is /etc/default/grub (I'm in Debian now so I can't verify exactly). Read the [Ubuntu Wiki page on Grub2.]("https://help.ubuntu.com/community/Grub2"). From the page:
> The primary configuration file for changing menu display settings is /etc/default/grub.
> The main menu file, /boot/grub/grub.cfg, is not meant to be edited, even by 'root'. 

Edit: Heh, I see you were one minute faster WorMzy.

---

### Post by drs305 on 2010-11-29
The instructions on how to make the change are in the following guide, which doesn't go into as much detail as the other Grub2 guides I've written. But it gives you what you need to know:
[Grub 2 - 5 Common Tasks]("http://ubuntuforums.org/showthread.php?t=1302743")

You might also want to install StartUp-Manager, which can set the default OS and timeout via a very simple GUI.
```

sudo apt-get install startupmanager

```
Run it via System, Administration, StartUp-Manager.

---

### Post by MorrisseyJ on 2010-11-30
Thank you all very much. Clear instructions and problem solved. 

Bit irritated with myself for not spotting this online, so thanks again for the help.

---

### Post by wilee-nilee on 2010-11-30
> **MorrisseyJ said:**
> Thank you all very much. Clear instructions and problem solved. 

Bit irritated with myself for not spotting this online, so thanks again for the help.

Many miss this it is alright.;)

---

