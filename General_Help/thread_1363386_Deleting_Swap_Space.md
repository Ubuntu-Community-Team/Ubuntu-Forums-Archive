---
title: "Deleting Swap Space"
date: 2009-12-24
forum: General Help
---

### Post by killians31 on 2009-12-24
Hey guys,

Quick question - I performed a search and didn't quite find what i was looking for.

I will be installing another operating system very shortly, appearently this operating system needs to be on a primary partition, which i do not have available.

Here is my current partition table:

sda1 | Windows Seven
 --------sda2-----------
 sda5 | /boot Ubuntu  
 sda6 | /Ubuntu       
 sda7 | /boot Fedora  
 sda8 | /Fedora       
 sda9 | /Backtrack     
 -------------------------
 sda3 | Shared Drive  
 sda4 | Swap

If i delete my Swap directory (which all of my Linux distributions are tied too), will it affect or damage any of the operating systems?

Thanks,
Ben

---

### Post by bumanie on 2009-12-24
I know for a fact that ubuntu can operate without /swap, as I tried it like that for a while, just to see what would happen. As far as I remember, I got a message that there was no /swap, but otherwise the system ran fine. I don't know about fedora, but would assume it can too. If one has 2gb+ of ram /swap is rarely used unless one is doing extremely heavy video encoding or something like that. You can always try and if things don't work, reinstall swap by gparted.

---

### Post by QLee on 2009-12-24
[QUOTE=killians31]Hey guys,

Quick question - I performed a search and didn't quite find what i was looking for.[/QUOTE]

Hummm, wonder what you searched for and where.

[QUOTE=killians31]I will be installing another operating system very shortly, appearently this operating system needs to be on a primary partition, which i do not have available.[/QUOTE]

This would have been a good place to identify which OS you are referring to, in case it matters to the answer.

[QUOTE=killians31]
If i delete my Swap directory (which all of my Linux distributions are tied too), will it affect or damage any of the operating systems?[/QUOTE]

Do you mean delete the swap partition? There is no swap "directory".

How much space is there in that swap partition? Will it be enough for the OS you want to install in a primary? If you have to carve up existing partitions and recombine to get a partition large enough for the install, then yes, there is considerable potential to muck things up for one or all of the other OSs. But, it could be done successfully, make sure you understand what you are going to do before you give any commands or do any clicking.

---

### Post by killians31 on 2009-12-24
The swap partition is only 1 GB, so i would need to shift around the space within certain partitions.

I was just concerned that if i delete the swap partition, after all of the distributions have already been configured for it, it would cause some errors.

---

### Post by adam814 on 2009-12-24
You might need to "unconfigure" Ubuntu and Fedora to look for the partition.

Ubuntu and Fedora will both have references to the swap partition in /etc/fstab you'll need to comment out.

In Ubuntu you'll probably have to edit /etc/uswsusp.conf to comment out the resume line (Note that you'll be unable to hibernate) and rebuild the initrd image with "update-initramfs -u -k all"

Fedora may have a similar setup, I don't know if it uses uswsusp or not.

---

### Post by killians31 on 2009-12-24
> **adam814 said:**
> You might need to "unconfigure" Ubuntu and Fedora to look for the partition.

Ubuntu and Fedora will both have references to the swap partition in /etc/fstab you'll need to comment out.

In Ubuntu you'll probably have to edit /etc/uswsusp.conf to comment out the resume line (Note that you'll be unable to hibernate) and rebuild the initrd image with "update-initramfs -u -k all"

Fedora may have a similar setup, I don't know if it uses uswsusp or not.

Thats what i was unsure about, if i just delete the swap partition, will ubuntu give me an error because it can't find the swap partition in which it has been configured for?

p.s. i have 4 GB's of RAM, so i don't think i even really need a swap partition

---

### Post by adam814 on 2009-12-24
If you have 4GB of RAM and don't need to suspend to disk I doubt you'll have trouble without a swap partition unless you do a lot of video editing for example.

---

### Post by killians31 on 2009-12-24
If i delete the swap partition without changing any configuration files, would there be any issues within ubuntu at bootup?

---

### Post by adam814 on 2009-12-24
I've never tried it myself.  I would imagine you'd at least get a message in your logs about being unable to find the resume device.

As for whether it would stop during the boot process and prompt you for it I don't know.  You could try it out before you do any other partition shifting (just delete the swap partition) and make sure you have a LiveCD or GParted LiveCD handy to restore it in case it does keep you from booting.

---

### Post by louieb on 2009-12-24
> **killians31 said:**
> If i delete the swap partition without changing any configuration files, would there be any issues within ubuntu at bootup?

Linux will print some messages out about not finding swap. But should boot anyway.
Find the line that defines swap in **/etc/fstab **and remove or comment it out. 
[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=283131")

---

