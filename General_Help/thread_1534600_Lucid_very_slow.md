---
title: "Lucid very slow"
date: 2010-07-19
forum: General Help
---

### Post by xcv on 2010-07-19
Hello to everyone, this is my first post in this forum, excuse me for my english, its not my language

I began in linux using opensuse 11.2, it worked perfectly to me and it made me want to try other distributions. I heard a lot about ubuntu so i decided to try it. Some weeks ago (about 2 or 3) i installed lucid in my computer. Everything was ok, only the wired connection gave me problems but it didn't take more than one day (the DNS was wrong XD)

Lastly i have compared both distros to choose one for my daily use, but i have realised that something has to be wrong in my ubuntu, because anything uses a lot of CPU, here are some examples:

gnome-terminal  -> About 50%
compiz (when using effects) -> 60%-70%
synaptic -> 100% !!!!!
Firefox -> 50%-60%
System monitor -> 30%-40%

(Imagine what happens if i use all them at the same time... My computer keeps its physical integrity and I don't know why... it should be molten; in opensuse sometimes I have the four desktops in use and it works like there just was a notepad running, including the desktop effects and games)

And I think that its not my hardware, its not bad in my opinion:

CPU:  3.2 GHz dual core
RAM:  1.5 GB ( 1 GB + 0.5 GB )
HD:   SATA 320GB: Extended: root 30GB  home 45 GB  swap 3 GB
Graphics card:  Nvidia GeForce 6200  (the driver is installed and working)

If you need more information do not hesitate to ask

Compared to my opensuse with kde4 (which i have heard about being bulky compared with gnome or kde3) ubuntu works worse than a windows ME filled of viruses, and if so much people use ubuntu its not possible to be so slow.

Thank you in advance

PD: I repeat, the nvidia driver is installed and working perfectly:
$ hwinfo --gfx
26: PCI 100.0: 0300 VGA compatible controller (VGA)             
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_10de_221
  Unique ID: VCu0.b676ZhNYTM5
  Parent ID: vSkL.S16qDHSKEeD
  SysFS ID: /devices/pci0000:00/0000:00:01.0/0000:01:00.0
  SysFS BusID: 0000:01:00.0
  Hardware Class: graphics card
  Model: "nVidia GeForce 6200 (0x0221)"
  Vendor: pci 0x10de "nVidia Corporation"
  Device: pci 0x0221 "GeForce 6200 (0x0221)"
  SubVendor: pci 0x1458 "Giga-byte Technology"
  SubDevice: pci 0x343c 
  Revision: 0xa1
  Driver: "nvidia"
  Driver Modules: "nvidia"
  Memory Range: 0xfd000000-0xfdffffff (rw,non-prefetchable)
  Memory Range: 0xc0000000-0xcfffffff (rw,prefetchable)
  Memory Range: 0xfc000000-0xfcffffff (rw,non-prefetchable)
  Memory Range: 0xfeae0000-0xfeafffff (ro,prefetchable,disabled)
  IRQ: 16 (120339 events)
  I/O Ports: 0x3c0-0x3df (rw)
  Module Alias: "pci:v000010DEd00000221sv00001458sd0000343Cbc03sc00i00"
  Driver Info #0:
    XFree86 v4 Server Module: nv
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #15 (PCI bridge)

Primary display adapter: #26

---

### Post by xcv on 2010-07-20
I'm sorry for the double post but I really need help, I asked in other forums and nobody posted any answer. Here the same is happening and this thread was after page 12 in the second day...

---

### Post by xcv on 2010-08-14
Nobody answers to me and i'm getting tired of this "nice" community

Lastly i have been using the top command just after turning on and i have seen that Xorg and compiz both use about 50-60% (each)

I have also thought that it could be a problem that it is launched with opensuse 11.2's grub 1, this is the menu.lst lucid entry
```

###Don't change this comment - YaST2 identifier: Original name: linux###
title Ubuntu 10.04 LTS (Lucid)
    root (hd0,7)
    kernel /boot/vmlinuz-2.6.32-23-generic root=UUID=ea9c930c-10db-446b-b93e-59b24d050852 ro quiet splash
    initrd /boot/initrd.img-2.6.32-23-generic
```It also checks the disk every time it starts, is it normal? The splash screen is also 800x600 and it appears some seconds after i choose it from the list, during that time, it displays this menu.lst entry

---

### Post by quequotion on 2010-08-20
not many of my threads get replies either ;)

Those CPU percentages are definitely strange. Compiz is a known hog, but 70% is a bit overboard even for it. Gnome-terminal should use next to nothing unless it has a process running in it.

Have you filed a bug report in lauchpad? Always take a look there and report something if you can't find an issue like your own.

Your grub entry looks ok and I also use grub legacy with Lucid. As far as I can tell that shouldn't be making your pc slow.

If you find in grub's kernel line the parameter "profile" *that definetly would make your computer slow and all processes use too much cpu*, but it isn't there so....

Could you get a screenshot of gnome-system-monitor showing all processes in tree view?

Frankly I have no idea what could be wrong with your installation, but If there's anything I can do I'll try to help.

---

### Post by quequotion on 2010-08-20
> **xcv said:**
> Nobody answers to me and i'm getting tired of this "nice" community

Lastly i have been using the top command just after turning on and i have seen that Xorg and compiz both use about 50-60% (each)

I have also thought that it could be a problem that it is launched with opensuse 11.2's grub 1, this is the menu.lst lucid entry
```

###Don't change this comment - YaST2 identifier: Original name: linux###
title Ubuntu 10.04 LTS (Lucid)
    root (hd0,7)
    kernel /boot/vmlinuz-2.6.32-23-generic root=UUID=ea9c930c-10db-446b-b93e-59b24d050852 ro quiet splash
    initrd /boot/initrd.img-2.6.32-23-generic
```It also checks the disk every time it starts, is it normal? The splash screen is also 800x600 and it appears some seconds after i choose it from the list, during that time, it displays this menu.lst entry

There are some issues with the splash screen (plymouth) and nvidia. You'll have to add the resolution you want to grub entries manually to get it right (I have a how-to thread about this, to which no one has replied)

What kind of disk configuration do you have? (SATA, IDE, RAID, etc)

---

