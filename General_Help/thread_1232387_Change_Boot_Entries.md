---
title: "Change Boot Entries"
date: 2009-08-05
forum: General Help
---

### Post by Kiriefotia on 2009-08-05
How do I do this?

I have Ubuntu & XP Pro dual boot on 1 HD
As it stand I have 
"Windows XP Professional"
"Ubuntu"
"(Windows Default)

After selecting Ubuntu options come up for CLI, GUI, Recovery mode etc

I want my boot screen to say

1 Windows XP Professional
2 Ubuntu CLI 

And have XP Pro as the default

Also, how do I remove (Windows Default) from the boot entries? It does not show in cmd BOOTCFG

---

### Post by BslBryan on 2009-08-05
Navigate to Applications --> Accessories --> Terminal, and type in
```
gksudo gedit /boot/grub/menu.lst
```

There will be two entries.  Simply cut and paste the entries in the order you would like for them to appear.

Regards!

---

### Post by Kiriefotia on 2009-08-05
hmm well my first post was what I saw in a previous Version of Ubuntu, the new one (i just installed yesterday) has no option for CLI mode?? why not???

After selecting Ubuntu the options show up

kernal xx.xx.xx
kernal xx.xx.xx (recovery)
kernal yy.yy.yy
kernal yy.yy.yy (recovery)
mem test

What happened to the boot in CLI mode? or how do I add it?



You reponse pointed me in the right direction but I didn't get it.



## ## End Default Options ##

title        Ubuntu 9.04, kernel 2.6.28-14-generic
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=A050B2CC50B2A904 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd        /boot/initrd.img-2.6.28-14-generic

title        Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=A050B2CC50B2A904 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
initrd        /boot/initrd.img-2.6.28-14-generic

title        Ubuntu 9.04, kernel 2.6.27-7-generic
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=A050B2CC50B2A904 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 9.04, kernel 2.6.27-7-generic (recovery mode)
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=A050B2CC50B2A904 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 9.04, memtest86+
root        ()/ubuntu/disks
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows NT/2000/XP
root        (hd0,0)
savedefault
chainloader    +1

this is what menu.lst says but on the boot screen it shows
Windows XP Pro
Ubuntu

Then after you select Ubuntu the extra options come up. the first menu, I do not see in menu.lst and that is wehere I want it to be. So that I do not need a submenu of Ubuntu
And if there is a way, please tell, how to add Ubuntu CLI to the menu.lst
Thanks

---

