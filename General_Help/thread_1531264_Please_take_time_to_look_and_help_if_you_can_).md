---
title: "Please take time to look and help if you can :)"
date: 2010-07-14
forum: General Help
---

### Post by HenneBaby02 on 2010-07-14
I have a dell Dimension 2350, which is a old school comp about 7-8 years old...im currently using ubuntu 10.04.. but it's not worth it due to the crashing and mouse cursor disapears in 1024x768 mode, so imma downgrade back to ubuntu 8.04. Which reconizes my graphics driver. But my only problem with it is.. When i switch from 800x600 to 1024x768 my screen (14 inch Dell monitor) i get maybe 10 inches out of it with the respected mode (working) but cut off. Then when i revert back to 800x600 the screen slides from left to right at a rapid pace... So basically what i wanted to know is if there is a fix to that, if anyone remembers or had the same issue.. heres my Comp's Info


09: PCI 02.0: 0300 VGA compatible controller (VGA)              
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_8086_2562
  Unique ID: _Znp.7NKSmo3TGAF
  SysFS ID: /devices/pci0000:00/0000:00:02.0
  SysFS BusID: 0000:00:02.0
[B]  Hardware Class: graphics card
  Model: "Intel i845"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x2562 "i845"
  SubVendor: pci 0x1028 "Dell"
  SubDevice: pci 0x0147 [/B]
  Revision: 0x03
  Memory Range: 0xe0000000-0xe7ffffff (rw,prefetchable)
  Memory Range: 0xee000000-0xee07ffff (rw,non-prefetchable)
  IRQ: 16 (25716 events)
  I/O Ports: 0x3c0-0x3df (rw)
  Module Alias: "pci:v00008086d00002562sv00001028sd00000147bc03sc00i00"
  Driver Info #0:
    XFree86 v4 Server Module: intel
  Driver Info #1:
    XFree86 v4 Server Module: intel
    3D Support: yes
    Extensions: dri
  Config Status: cfg=new, avail=yes, need=no, active=unknown

Primary display adapter: #9


I'd really appreciate any help. Thank you in advance and if i take a little while to respond don't worry i didn't do a post and run :p i'm gonna downgrade after i post this.

---

### Post by mörgæs on 2010-07-14
Ubuntu 10.04 and the Intel 845 are not good friends. 

I would try this: 
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

or install 9.10 (not 8.04, since the drivers have improved a lot).

---

### Post by HenneBaby02 on 2010-07-14
> **mörgæs said:**
> Ubuntu 10.04 and the Intel 845 are not good friends. 

I would try this: 
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

or install 9.10 (not 8.04, since the drivers have improved a lot).


thanks for the reply, i kno  8.04 isn't as good as 9.10 and i have tried that but after trying

$sudo add-apt-repository ppa:glasen/intel-driver 
then
$ sudo apt-get update && sudo apt-get upgrade

it says the glasen repo isn't available but i also wanna take advantage of visual effects this bein my first time using em and i love it so far :)

EDIT: besides the fact that i wanna use the visual effects, ubuntu 9.10 doesn't cause a problem for me. ill keep searchin about 8.04 though. Basically though all i wanna do is use 1024x768 mode without my screen getting cut off :)

---

### Post by HenneBaby02 on 2010-07-15
> **mörgæs said:**
> 
or install 9.10 (not 8.04, since the drivers have improved a lot).

thank you once again for takin the time to reply, i jus upgraded back to ubuntu 9.10 once again lol since i couldn't find a fix to the issue. i guess this is my last run before i jus stay with windows at least til i get a better computer i guess.

---

### Post by mörgæs on 2010-07-15
You are welcome.

A used computer a few years old would be great for Ubuntu, but still yours should be able to run fine. 

Regarding the PPA: If a repository is not available, best is just to wait a day and try again. Of course, this is not relevant now, since 9.10 does not need this.

---

### Post by HenneBaby02 on 2010-07-16
> **mörgæs said:**
> You are welcome.

A used computer a few years old would be great for Ubuntu, but still yours should be able to run fine. 

Regarding the PPA: If a repository is not available, best is just to wait a day and try again. Of course, this is not relevant now, since 9.10 does not need this.
Yea 9.10 doesn't cause a problem though it did freeze on me twice which is no biggy, it just sucks not bein able to use ubuntu to its fullest w/ effects :P

---

