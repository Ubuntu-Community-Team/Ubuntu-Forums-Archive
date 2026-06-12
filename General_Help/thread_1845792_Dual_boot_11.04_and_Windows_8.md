---
title: "Dual boot 11.04 and Windows 8???"
date: 2011-09-17
forum: General Help
---

### Post by yusuo85 on 2011-09-17
So I'm trying to get a good setup on my laptop, I got Windows 8 dev and Ubuntu 11.04 running at the moment.

I installed Ubuntu first and then Installed Windows 8, used a live usb to re-establish grub but grub won't see Windows 8, which means for the time being I'm locked out of my Windows partition.

Heres my fdisk -l
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        6086    48884736   83  Linux <-- Ubuntu
/dev/sda2            6087        6208      975873    5  Extended
/dev/sda3   *        6208       30402   194335744    7  HPFS/NTFS <-- Win8
/dev/sda5            6087        6208      975872   82  Linux swap / Solaris


And in the link below is a copy of my grub.cfg file 
[http://pastebin.com/Lvf3pW8D]("http://pastebin.com/Lvf3pW8D")

Any advice on how I can get these 2 living in harmony

Edit: Reloaded the update option in grub and now its working sorry all

---

### Post by htb2050 on 2011-09-23
CAn you explain it to me how to restore windows 8? i am new to linux and i installed the oneric ocelot beta 2 and there is no windows option in grub boot loader.

---

### Post by oldfred on 2011-09-23
@htb2050

This thread is solved as the OP found it works. I notice grub2's os-prober saw Windows 8 as a recovery environment.
Did you try?
sudo update-grub

You are also running 11.10 which is still beta which may have other issues also. Please start a new thread in the Ubuntu +1 (Oneiric Ocelot) sub forum. It would also help to post boot script to see your exact configuration.
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

