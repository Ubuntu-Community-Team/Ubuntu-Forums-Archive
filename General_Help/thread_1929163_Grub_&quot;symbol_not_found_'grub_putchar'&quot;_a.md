---
title: "Grub &quot;symbol not found 'grub_putchar'&quot; and &quot;incompatible license&quot;"
date: 2012-02-21
forum: General Help
---

### Post by rusljam on 2012-02-21
Hi!

I have 2 hard drives: sda and sdb that have these partitions: 
1. **sda1** (boot for Ubuntu_10.04) 2. **sda2** (swap) 3. **sda3** (root for Ubuntu_10.04) 4. **sda4** (home for Ubuntu_10.04) 5. **sdb1** (fat32 for all stuff for Windows) 6. **sdb2** (root for Debian) 7. **sdb3** (root for Ubuntu_12.04) 8. **sdb4** (ext4 as usb stick for Linux).

**Sda** is a scsi hard drive and **sdb** is an usb hard drive. There are installed **Ubuntu_10.04,** **Debian** and **Ubuntu_12.04** (these two on **sdb**).

Well, after I’ve installed Debian, and disconnected the usb hard drive I’ve got a grub rescue prompt. This is normal (Debian was first in grub list). There were two problems: 
1. when I tried to load a kernel of Ubuntu_10.04 I got a message "incompatible license". Not a solution but why is it there is [here]("http://ubuntuforums.org//http://us.generation-nt.com/answer/bug-650435-grub-pc-recsue-mode-doesnt-rescue-error-incompatible-license-help-205594961.html").
2. When I tried to load a kernel from grub rescue prompt (this was after change one Debian for another) I got this: "symbol not found 'grub_putchar'". 

What is it and how can I load a kernel from grub rescue prompt?

The problem not is to boot an OS, I can it pretty well. The problem is [SIZE=2][COLOR=Black]_**how can I do this from grub rescue prompt?**_[/COLOR][/SIZE]

---

### Post by roelforg on 2012-02-21
See: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
Chapter: [SIZE=1]Command Line and Rescue Mode[/SIZE]

---

### Post by rusljam on 2012-02-21
Thanks! But I’d read it before to proceed. And when I did it (as described [there]("https://help.ubuntu.com/community/Grub2")) I got my problem.

insmod normal
Insmod linux
And other combinations give me "symbol not found 'grub_putchar'". What is it? And what solution is?

---

### Post by oldfred on 2012-02-21
It may be incompatible grubs from Debian and Ubuntu even though they are both grub2. The newest version of grub2 can only be updated with a liveCD of the same version.

I might try this and run the boot info script to see details of your installs:

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

---

### Post by rusljam on 2012-02-22
Well, thank you very much! This seems to be many incompatibilities between different versions of Grub2. Trying many combinations I understood that Grub2 from Debian from rescue mode does  not working with Grub2 from ubuntu_10.04 (v-1.98 ) (I am not sure about vice versa). Grub2 from Ubuntu_10.04 is incompatible (license matters) with Grub2 from Ubuntu_12.04. And Grub2 from Ubuntu_12.04 simply doesn&#8217;t working on my machine (Amd Athlon 64-bit), it seems to be wrong graphical settings because when booting the monitor seems to have being disconnected from graphical card (and this is not the case).

---

### Post by oldfred on 2012-02-22
Is it a grub setting gfxmode or a setting you add to grub to get system to boot like nomodeset?

Natty or later Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

Resetting an out&#8208;of&#8208;range resolution (does not include grub's set gfxmode=640x480)
[https://wiki.ubuntu.com/X/Config/Resolution#Resetting_an_out-of-range_resolution](https://wiki.ubuntu.com/X/Config/Resolution#Resetting_an_out-of-range_resolution)
Repair grub's video mode and other settings
[https://launchpad.net/grub-customizer](https://launchpad.net/grub-customizer)

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

