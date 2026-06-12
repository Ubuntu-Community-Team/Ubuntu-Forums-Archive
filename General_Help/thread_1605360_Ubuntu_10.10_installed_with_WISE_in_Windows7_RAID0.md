---
title: "Ubuntu 10.10 installed with WISE in Windows7 RAID0"
date: 2010-10-25
forum: General Help
---

### Post by Molder2k on 2010-10-25
Hi All,
Hi have a M1730 with 2 HD in RAID 0. Windows 7 64bit installed. 

I tried to install Ubuntu 10.10 with WUBI, all ok the installation in Windows.
Restarted the system I have 2 multiboot options with the new Ubuntu...  it starts but in graphic mode it tries to finish the installation and  stops with an error message like that: "root filesystem not defined...".

The problem is the raid0 of my disks or other?

Thanks

---

### Post by Hippytaff on 2010-10-25
Not sure about WISE, but if you want to install ubuntu in windows (as opposed to a seperate real partition) it's probably best to use wubi...though it looks as though the the root partition / hasn't been installed or is not defined. I would suggest booting from live cd and fixing it this way, but I'm out of my depth with WISE :-) Alteranitvely install it with wubi in windows, or do a real partition install.

---

### Post by Molder2k on 2010-10-25
OPS!! WUBI!!! I wrote wise but I can't modify my post:(

I would like to try ubuntu 10.10 in HD without a new partition. With the disks in raid I don't want to risk to unable boot again windows in grub troubles conditions:(

---

### Post by Hippytaff on 2010-10-25
ah...theres an edit button in the bottom right of the post window...in that case it might be worth having a read of this [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

but I never resolved the exact same issue whilst trying to install jolicloud on my wifes laptop.

you can always try ubuntu from liveCD :-)

---

### Post by Molder2k on 2010-10-25
I have already read all the guide but nothing... This afternoon I will try to run the WUBI Installation with administrator privileges in Windows...

The LIVE Cd works very well..!

---

### Post by Hippytaff on 2010-10-25
> **Molder2k said:**
> administrator privileges 
that mighty very well be the issue

---

