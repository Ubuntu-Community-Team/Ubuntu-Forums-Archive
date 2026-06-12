---
title: "Grub does not show up"
date: 2012-03-30
forum: General Help
---

### Post by BobRoss2666 on 2012-03-30
I recently dual boot installed ubuntu 11.10 onto my windows vista machine and now I cannot use my Windows vista OS. What can I do to fix this?

---

### Post by JC Cheloven on 2012-03-30
Can you boot in Ubuntu?

---

### Post by Bucky Ball on 2012-03-30
Welcome.

If you are not getting a menu at boot (as your thread title suggests) try hitting escape (or shift, not sure for 11.10) after the BIOS at boot and that should give you a menu. Windows should be on there ...

---

### Post by drs305 on 2012-03-30
Welcome to the Ubuntu Forums.

Your problem could be as simple as Grub not yet recognizing Windows and thus failing to put it in the boot menu.

The easiest thing to try is to use the Boot Repair tool. If it doesn't fix things, it will offer to run a script which can provide us more information about your system.

Here is the Boot Repair thread link:
[http://ubuntuforums.org/showthread.php?t=1769482]("http://ubuntuforums.org/showthread.php?t=1769482")

---

### Post by JC Cheloven on 2012-03-30
Hi again, 
I wish it's all about something simple and easy, as the other members suggest. But perhaps, before attempting any repair, it would be desirable to know what your exact situation is (in the worst case you may have accidentally overwritten you vista partition, let's hope not). 

So, to help us giving a more precise advice, if you can boot in ubuntu (?), could you please open a terminal, type in ```
sudo fdisk -l
```and post back the output here?
Thank you
JC

---

### Post by pellyhawk on 2012-03-30
> **BobRoss2666 said:**
> I recently dual boot installed ubuntu 11.10 onto my windows vista machine and now I cannot use my Windows vista OS. What can I do to fix this?

try boot with live cd or usb, then do:
```
sudo update-grub
```

---

### Post by BobRoss2666 on 2012-03-31
@ JC Cheloven

Heres the output:

Disk /dev/sda: 250.1 GB, 250059350016 bytes
240 heads, 63 sectors/track, 32301 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   472303439   236151688+   7  HPFS/NTFS/exFAT
/dev/sda3       472303440   488391119     8043840    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00086497

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048    97656831    48827392   83  Linux
/dev/sdb2        97658878   103516159     2928641    5  Extended
/dev/sdb5        97658880   103516159     2928640   82  Linux swap / Solaris

---

### Post by BobRoss2666 on 2012-03-31
> **drs305 said:**
> Welcome to the Ubuntu Forums.

Your problem could be as simple as Grub not yet recognizing Windows and thus failing to put it in the boot menu.

The easiest thing to try is to use the Boot Repair tool. If it doesn't fix things, it will offer to run a script which can provide us more information about your system.

Here is the Boot Repair thread link:
[http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482)

The repair did not work but I did run Summary and here it is:

[HTML]http://paste.ubuntu.com/908273/plain/[/HTML]

---

### Post by Bucky Ball on 2012-03-31
Are you getting a menu at boot or is it going straight to Ubuntu boot? If no list of choices, hit escape or shift (not sure which in your release) to get one and see if Windows is there. (Repeating myself but not clear that you've tried this.) 

In Ubuntu open a terminal and try:

```
sudo update-grub
```... as previously suggested (although no need to boot from the LiveCD).

From the looks of your terminal output all is as it should be; Windows on sda and Ubuntu on sdb ...

---

### Post by drs305 on 2012-03-31
Let's first try to get Windows working again.  I'm assuming you are able to boot Ubuntu without using a LiveCD.

It looks like Grub was written to the MBRs of both sda and sdf drives. To restore the Windows bootloader to sda (250GB) drive, you can use the Windows repair tool or do it from the Ubuntu Desktop.

Assuming you are on the Desktop, install an app called 'lilo' and run the following commands. It will install lilo and then rewrite your sda MBR to point to the Windows boot files. You will get messages about needing to configure lilo, but only run these two commands. Open a terminal (ATL-F2, gnome-terminal)

```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

```
If you reboot and select sda to boot first in BIOS, you should see your Windows menu. If you select sdf to boot first, you should get Ubuntu. 

Once they are working independently, you can try to get them both working from the Grub menu. In Ubuntu, you can try to run the "sudo update-grub" command again. Although the Windows entry is already in the Grub menu, which is what we normally use the command to do, it might trigger the Grub menu to display at boot.

---

### Post by BobRoss2666 on 2012-04-03
Everything works beautifully now! Thank you so much!

---

### Post by Bucky Ball on 2012-04-03
> **BobRoss2666 said:**
> Everything works beautifully now! Thank you so much!

Excellent news! Enjoy ...

Could you please mark thread as 'Solved' to help others. ;)

---

