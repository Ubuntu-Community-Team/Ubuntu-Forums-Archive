---
title: "Anyone with a Nvidia GeForce FX 5200: HELP ME!"
date: 2006-04-11
forum: General Help
---

### Post by Matt342 on 2006-04-11
Hello Ubuntu Users,

When I try to boot up my PC normally with Ubuntu (or any other Linux Distro) everything works. When I use my Nvidia GeForce FX 5200 Video Card I get a "KERNEL PANIC" error. What is the problem?

Matt

---

### Post by taurus on 2006-04-11
Kernel panic for a nVidia video card!  I have eVGA GeForce FX5600 which I think it's almost identical to FX5200 and it is working just fine!  What is the content of your /boot/grub/menu.lst.  Open a terminal by clicking Applications -> Accessories -> Terminal and type
```

sudo more /boot/grub/menu.lst

```
Now, paste the output on your screen here then...

---

### Post by Matt342 on 2006-04-11
What do I do if I cannot boot into the system?

Matt



[QUOTE=taurus]Kernel panic for a nVidia video card!  I have eVGA GeForce FX5600 which I think it's almost identical to FX5200 and it is working just fine!  What is the content of your /boot/grub/menu.lst.  Open a terminal by clicking Applications -> Accessories -> Terminal and type
```

sudo more /boot/grub/menu.lst

```
Now, paste the output on your screen here then...[/QUOTE]

---

### Post by Matt342 on 2006-04-11
What do I do if I cannot boot into the system?

Matt



[QUOTE=taurus]Kernel panic for a nVidia video card!  I have eVGA GeForce FX5600 which I think it's almost identical to FX5200 and it is working just fine!  What is the content of your /boot/grub/menu.lst.  Open a terminal by clicking Applications -> Accessories -> Terminal and type
```

sudo more /boot/grub/menu.lst

```
Now, paste the output on your screen here then...[/QUOTE]

---

### Post by Matt342 on 2006-04-11
What do I do if I cannot boot into the system?

Matt



[QUOTE=taurus]Kernel panic for a nVidia video card!  I have eVGA GeForce FX5600 which I think it's almost identical to FX5200 and it is working just fine!  What is the content of your /boot/grub/menu.lst.  Open a terminal by clicking Applications -> Accessories -> Terminal and type
```

sudo more /boot/grub/menu.lst

```
Now, paste the output on your screen here then...[/QUOTE]

---

### Post by taurus on 2006-04-11
Do I hear an echo in here???  :) 

Can you boot into a recovery mode from GRUB?  If not, then you need to download the LiveCD and boot from it.  Then, open a terminal and mount your harddrive (or at least the partition that contains /boot) somewhere so you can read the GRUB's menu from your LiveCD.

---

### Post by Matt342 on 2006-04-11
The web site was not working. Thats why the echo was present. Sorry :-D

I booted when I removed the GeForce. Here is the file:

# Modified by YaST2. Last modification on Wed Apr 12 00:01:34 UTC 2006

color white/blue black/light-gray
default 0
timeout 8
gfxmenu (hd0,5)/boot/message

###Don't change this comment - YaST2 identifier: Original name: linux###
title SUSE LINUX 10.0
    root (hd0,5)
    kernel /boot/vmlinuz root=/dev/sda6 vga=0x317 selinux=0    resume=/dev/sda5  splash=silent showopts
    initrd /boot/initrd

###Don't change this comment - YaST2 identifier: Original name: windows 1###
title windows 1
    chainloader (hd0,0)+1

###Don't change this comment - YaST2 identifier: Original name: windows 2###
title windows 2
    chainloader (hd0,1)+1

###Don't change this comment - YaST2 identifier: Original name: windows 3###
title windows 3
    chainloader (hd1,0)+1

###Don't change this comment - YaST2 identifier: Original name: floppy###
title Floppy
    chainloader (fd0)+1

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- SUSE LINUX 10.0
    root (hd0,5)
    kernel /boot/vmlinuz root=/dev/sda6 vga=normal showopts ide=nodma apm=off acpi=off noresume selinux=0 nosmp noapic maxcpus=0 edd=off 3
    initrd /boot/initrd




----------------

Matt
[QUOTE=taurus]Do I hear an echo in here???  :) 

Can you boot into a recovery mode from GRUB?  If not, then you need to download the LiveCD and boot from it.  Then, open a terminal and mount your harddrive (or at least the partition that contains /boot) somewhere so you can read the GRUB's menu from your LiveCD.[/QUOTE]

---

### Post by taurus on 2006-04-11
Wait a second!!!  This is SUSE 10.0!!!  Are you talking about the vga=0x317 option?

---

### Post by Matt342 on 2006-04-11
Yeah! I put Suse on there. Can you still help me?

Matt






[QUOTE=taurus]Wait a second!!!  This is SUSE 10.0!!!  Are you talking about the vga=0x317 option?[/QUOTE]

---

### Post by Matt342 on 2006-04-11
What is 
vga=0x317?

Matt

[QUOTE=taurus]Wait a second!!!  This is SUSE 10.0!!!  Are you talking about the vga=0x317 option?[/QUOTE]

---

### Post by taurus on 2006-04-11
But of course.  I can still help you BUT I will have to charge you now!!!  :) 

vga=0x317 is just a video mode for SUSE when it boots.  It is safe to remove it from your kernel entry though.

---

### Post by Matt342 on 2006-04-12
So Please Help Me!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!:KS 


[QUOTE=taurus]But of course.  I can still help you BUT I will have to charge you now!!!  :) 

vga=0x317 is just a video mode for SUSE when it boots.  It is safe to remove it from your kernel entry though.[/QUOTE]

---

### Post by taurus on 2006-04-12
Have you tried removing "vga=0x317" from your kernel entry and see if it can boot now???

---

### Post by Matt342 on 2006-04-12
From /boot/grub/menu.st?

If so I tried that.

Matt
[QUOTE=taurus]Have you tried removing "vga=0x317" from your kernel entry and see if it can boot now???[/QUOTE]

---

### Post by bubi73 on 2006-04-12
I have a Chaintech FX5200 and had initial problems with it when installing Ubuntu. It would only let me choose 640x480 mode. After installing the latest nvidia drivers with automatix the problem was fixed.

---

### Post by Matt342 on 2006-04-12
How do I install the drivers if I cannot boot into the OS?

Matt

[QUOTE=bubi73]I have a Chaintech FX5200 and had initial problems with it when installing Ubuntu. It would only let me choose 640x480 mode. After installing the latest nvidia drivers with automatix the problem was fixed.[/QUOTE]

---

### Post by taurus on 2006-04-12
[QUOTE=Matt342]The web site was not working. Thats why the echo was present. Sorry :-D

I booted when I removed the GeForce. Here is the file:

# Modified by YaST2. Last modification on Wed Apr 12 00:01:34 UTC 2006

color white/blue black/light-gray
default 0
timeout 8
gfxmenu (hd0,5)/boot/message

###Don't change this comment - YaST2 identifier: Original name: linux###
title SUSE LINUX 10.0
    root (hd0,5)
    kernel /boot/vmlinuz root=/dev/sda6 vga=0x317 selinux=0    resume=/dev/sda5  splash=silent showopts
    initrd /boot/initrd

###Don't change this comment - YaST2 identifier: Original name: windows 1###
title windows 1
    chainloader (hd0,0)+1

###Don't change this comment - YaST2 identifier: Original name: windows 2###
title windows 2
    chainloader (hd0,1)+1

###Don't change this comment - YaST2 identifier: Original name: windows 3###
title windows 3
    chainloader (hd1,0)+1

###Don't change this comment - YaST2 identifier: Original name: floppy###
title Floppy
    chainloader (fd0)+1

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- SUSE LINUX 10.0
    root (hd0,5)
    kernel /boot/vmlinuz root=/dev/sda6 vga=normal showopts ide=nodma apm=off acpi=off noresume selinux=0 nosmp noapic maxcpus=0 edd=off 3
    initrd /boot/initrd
----------------

Matt[/QUOTE]
Again, try removing "vga=0x317" from the entry for kernel in /boot/grub/menu.lst so it would look something like this
```
title SUSE LINUX 10.0
    root (hd0,5)
    kernel /boot/vmlinuz root=/dev/sda6 selinux=0 resume=/dev/sda5  splash=silent showopts
    initrd /boot/initrd

```
](*,)

---

### Post by z_diver on 2006-04-12
I have a laptop with an Nvidia FX5200 go and i've put everything from Suse 9.2 to Dapper on it without an issue.  By chance, did you have the video card in the system when you installed?  Also, the first Suse 10 CD has a Rescue/Recovery option which works wonders in situations where hardware seems to be the culprit(like this).

I'd suggest running that and it will run Sax2 which will rewrite your xorg.conf and make sure you have the best drivers.  That should fix it.

---

### Post by Matt342 on 2006-04-12
How do I use Rescue Mode? It boots from a Remote login.

Matt

[QUOTE=z_diver]I have a laptop with an Nvidia FX5200 go and i've put everything from Suse 9.2 to Dapper on it without an issue.  By chance, did you have the video card in the system when you installed?  Also, the first Suse 10 CD has a Rescue/Recovery option which works wonders in situations where hardware seems to be the culprit(like this).

I'd suggest running that and it will run Sax2 which will rewrite your xorg.conf and make sure you have the best drivers.  That should fix it.[/QUOTE]

---

### Post by boonybooni on 2006-07-28
i had a similar problem with my FX 5200. i added intel-agp and agp_gart to the /etc/modprobe.d/blacklist file,but i dont know the specs of ur pc.

---

