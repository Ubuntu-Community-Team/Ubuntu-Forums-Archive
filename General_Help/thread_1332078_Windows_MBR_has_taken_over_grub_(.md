---
title: "Windows MBR has taken over grub :("
date: 2009-11-19
forum: General Help
---

### Post by JigglyWiggly_ on 2009-11-19
So I have a netbook 1005ha, I had installed Ubuntu 9.10, and it serves me well, I tried installing freebsd on it, and crap driver support, so I still had 100 gigs free. (I partitioned it one for Ubuntu, one for something else). Then I put windows xp pro sp3, on a usb...

Then it installed and now it can't boot into Windows, some generic error.

Unfortuantely it ate grub with it, I am back on the live cd (or usb in my case), and I need to get grub2 back. I would be fine with grub1, but grub2 is so much more confusing to me, I mean it used to be a menu.list file, now it's like... well I have no idea.

How do I get it back :(?

PS fdisk -l

/dev/sda1 = HPFS/NTFS 
/dev/sda2 = Extended
/dev/sda5 = Linux
/dev/sda6 = Linux swap/Solaris

---

### Post by oldfred on 2009-11-20
I hope these links help:

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)
Also reinstall grub2 using usb key
[https://wiki.ubuntu.com/KernelTeam/Grub2Testing](https://wiki.ubuntu.com/KernelTeam/Grub2Testing)

---

### Post by JigglyWiggly_ on 2009-11-20
grub-setup is an unrecognized, so I take it I want to install grub, there is no grub2 in synaptic, so I am assuming I am going to install grub-pc (this is version 2)

EDIT: Yes that is what I needed, and it works perfectly. Thanks so much!

---

