---
title: "can't pass grub rescue"
date: 2010-03-07
forum: General Help
---

### Post by Gnusboy on 2010-03-07
I have been trying to fix a broken Ubuntu 9.10 system. I cannot get past the "grub rescue" when booting from the 9.10 CD
I do NOT care about data loss. I want to install Ubuntu as if a clean install.
I used systemrescue64. used Gparted and believe I wiped the hard drive. Under Gparted, the drive shows as one continuous partition of 584 GB with an 10 GB extended partition and a 10 GB swap file
When I attempted to format the drive as Ext 4, the system locked up. I rebooted to retry it again and it froze both times. I could not open the CD drive during this and had to reboot to open the Cd drive and remove the rescue64 Cd.
I scanned the forums and found that 9.10 includes Ext 4, so I tried booting to the Ubuntu 9.10 disc, but keep getting the "grub rescue" prompt but it keeps refusing any command as an "Unknown command."

How do I get this thing working with a functioning Karmic OS?

My System info:
AMD Phenom X4
Asus M3A78-EM motherboard with onboard ATI Radeon 3200
4 GB ram
Western Digital 640 GB HDD

I've been trying to get the system up for more than 2 weeks. I have read hundreds of forum posts, tutorials and everything else I can find, but every answered question brings more questions and another lengthy search. I just can't do it anymore.

PLEASE HELP
Thank you.

---

### Post by sameer.walgude on 2010-03-12
Try this at grub rescue> prompt....

grub rescue> set prefix=(hd0,x)/boot/grub
grub rescue> insmod (hd0,x)/boot/grub/normal.mod
rescue:grub> normal


If still fails...boot up live cd...

at terminal...
sudo grub-setup -d /media/{kubuntu9.10partition}/boot/grub /dev/sda

substitute /media/{kubuntu9.10partition} with actual partition :)

If you get error message,(mapping fails), do this..

sudo grub-setup -d /media/{kubuntu9.10partition}/boot/grub -m 
/media/{kubuntu9.10partition}/boot/grub/device.map /dev/sda

All the best!

Thanks & Regards
Sameer J Walgude
[email]sameer.walgude@aol.in[/email]
+91 98191 15533

---

