---
title: "How do I install an operating system to an external drive."
date: 2011-06-26
forum: General Help
---

### Post by JohnBonne on 2011-06-26
I have tried to and failed at the attempt to install a second and third operating system on a windows partitioned hard drive. Something always happens to create a problem booting up. I.E:, the hard drive becomes un-bootable even with everything done according to book. 

I want to install ubuntu next to Windows or on a separate drive which is attached via usb cable.

I have Windows/Linux installed already using grub. I would need the three operating systems showing up on the boot portion of start-up.

Drive1. Windows Vista/Linux (installed using GRUB)

USB Drive2: Ubuntu or Mint.

Thank you.

---

### Post by JohnBonne on 2011-06-26
REPLY and BUMP

Really would like to do this before the weekend. It is just some gift to myself to install all these Operating Systems.

---

### Post by spiky001 on 2011-06-26
Can you explain what you have already got installed and where I.E on internal drive what is installed dose it work ok?

---

### Post by dragonfly41 on 2011-06-26
I would try **[COLOR=Navy]unetbootin[/COLOR]** .. either from windows or ubuntu .. to create a USB bootable version of Ubuntu or Mint

I've got Vista & ubuntu dual boot on /dev/sda/

and edubuntu on /dev/sdb/    (USB drive) .. plus backup partitions

---

### Post by oldfred on 2011-06-26
If your sda is a larger drive you can install there. You should partition in advance. Do you have a separate /home, you can only share if you use a different user ID which to me defeats the advantage. I prefer separate /shared NTFS partition for data you want to share with windows like Firefox & Thunderbird profiles and a separate /data for data files. Then your /home is a small  and a user only setting folder and you can keep it in / (root) and not have it as a separate partition.

If you want to install to the external you also need to do manual install so you get the option to install the grub2 boot loader to the external drive's MBR.

Installing Ubuntu in Hard Disk Two (or more) Maverick 10.10
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

---

