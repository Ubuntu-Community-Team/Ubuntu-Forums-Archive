---
title: "Restoring GRUB"
date: 2009-07-15
forum: General Help
---

### Post by fwc67 on 2009-07-15
Hello,
I just installed XP on a separate partition than my Ubuntu but it has erased Grub so I was wondering how to restore it using the live CD.  I went to the documentation in Ubuntu for restoring Grub but hit a snag in the instructions.
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
It says under the section of "Using the Ubuntu Desktop/Live CD" > 
You also need to mount your /boot partition if you made one, like this : 
```
mount /dev/sda1 /media/root/boot
```
To make sure it was the correct one, run ls /media/root/boot, which should output something like this : 
```
config-2.6.18-3-686      initrd.img-2.6.18-3-686.bak  System.map-2.6.18-3-686
grub                     lost+found                   vmlinuz-2.6.18-3-686
initrd.img-2.6.18-3-686  memtest86+.bin
```

I don't understand why you need to mount the boot partition under the partition that is already mounted.  If I go into the folder without following the step to mount like this "mount /dev/sda1 /media/root/boot" then I get the files they list anyway.  

Can someone please help explain whether I need to mount the boot partition or not, and if I do, how to determine which is the boot partition.  Common sense tells me its the one marked with the star when I run fdisk -l but that is also my Windows partition.  I hope its not complicated and thanks very much.

Edit: Also, at the bottom it says install it to the partition where you want to install GRUB.  Which partition is preferable?

---

### Post by rcayea on 2009-07-15
I am guessing you know how to boot to the live cd.

1. Boot into live CD.
2. Open terminal
3. type, "sudo grub"
4. type, "find /boot/grub/stage1"

"This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)" This quote I (Randy Cayea) am using was taken from a post on Ubuntu Forums. 

5.type, "root (hd?,?)"

"Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)" - This quote I (Randy Cayea) am using was taken from a post on Ubuntu Forums. 

6. type, "setup (hd0)"

7. quit

8. reboot

In all these commands don't use the quotes. 

Good Luck!

---

### Post by fwc67 on 2009-07-15
> **rcayea said:**
> I am guessing you know how to boot to the live cd.

1. Boot into live CD.
2. Open terminal
3. type, "sudo grub"
4. type, "find /boot/grub/stage1"

"This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)" This quote I (Randy Cayea) am using was taken from a post on Ubuntu Forums. 

5.type, "root (hd?,?)"

"Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)" - This quote I (Randy Cayea) am using was taken from a post on Ubuntu Forums. 

6. type, "setup (hd0)"

7. quit

8. reboot

In all these commands don't use the quotes. 

Good Luck!

Thank you, these steps work except I needed to mount the parition where my Linux was installed.  I appreciate it.

---

