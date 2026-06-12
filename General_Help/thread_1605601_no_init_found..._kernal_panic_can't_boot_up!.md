---
title: "no init found... kernal panic? can't boot up!"
date: 2010-10-25
forum: General Help
---

### Post by arnicainthemembrane on 2010-10-25
I have my computer partitioned with WinXP and Ubuntu. Noticing that the drive with windows on it was accessible from ubuntu, I started saving files there. It was around this time that it became impossible to boot up ubuntu. When I try, this is what I get:

Mount: mounting /dev/disk/by-uuid/151d6da2-e71f-412b-b022-a4e8fa688a9f on /root
failed: invalid argument
mount: mounting on /dev on /root/dev failed: no such file or directory
mount: mounting /sys on /root/sys failed: no such file or directory
mount: mounting /proc/ on /root/proc failed: no such file or directory

target system doesn't have /sbin/init
no init found. try passing init=bootary

BusyBox v1.13.3 (ubuntu 1:1.13.3- 1ubuntu11) built in shell (ash)

Enter 'help' for a list of built in commands.



(initramfs)_

... then if I type "exit" at this point:

/init: line 271: can't open /root/dev/console: no such file

[ 144.89035] kernal panic- not syncing: attempted to kill init!

... so there you have it! any explanations, suggestions, etc., hugely appreciated! thanks!

---

### Post by gzarkadas on 2010-10-26
This is the root cause of all that you see:

> **arnicainthemembrane said:**
> ...
Mount: mounting /dev/disk/by-uuid/151d6da2-e71f-412b-b022-a4e8fa688a9f on /root
failed: invalid argument
...

partition with UUID 151d6da2-e71f-412b-b022-a4e8fa688a9f (your only Ubuntu partition?) cannot be mounted. 

What to do:

1. Boot with your live CD or USB.

2. Fire-up Gparted and see what it says about your partitions. In particular:
Right-click your Ubuntu root partition and select `Information' from the context menu, then check the value of the `UUID' field. Or in a terminal type `sudo blkid' to see a list of all your partitions with device name (/dev/sd?) and UUID.

3. If your Ubuntu root partition has the expected UUID (151d6da2-e71f-412b-b022-a4e8fa688a9f), try to check it for errors. Run fsck in diagnose-only mode (replace ? with your partition's actual letter):
```
sudo fsck -V -n -v /dev/sd? | less
```4. Try to locate your syslog (/var/log/syslog in your original system; add in front of it /media/your-partition-name when accessing it from the live CD). Do a 
```
sudo cat /media/your-partition-name/var/log/syslog | tail -n 100 | less 
``` and see what error messages specific to mount appear (you may need to use 200 or a larger number in tail command).

5. If you can't figure out what's wrong and correct it, post your findings here; a copy of your /etc/fstab could also be helpful.

---

### Post by arnicainthemembrane on 2010-11-03
thanks for the advice. will do. Any idea what might have caused this?

---

### Post by gzarkadas on 2010-11-04
It's hard to tell from the initial post's description; it will be easier to find what happened when more data about the error (state of partitions, fsck results, etc.) are available.

---

### Post by arnicainthemembrane on 2010-11-08
Finding it nearly impossible to boot from usb: changed the bios and tried all the tricks I could find online but it still goes directly into the menu where you choose between windows and ubuntu, every time. My interest at this point is retrieving files from the ubuntu partition, saving them on my backup drive, then wiping the hard drive clean and starting all over with a new ubuntu distro. Is any of this possible without booting from usb? The computer I'm using to accomplish this is an Asus Eeepc1005HA.

---

### Post by gzarkadas on 2010-11-08
In principle it can be done from Busybox, since the essential utilities are there: you can mount your backup drive, then mount your ubuntu partition and copy files or use dd to copy the entire partition as an image file. But it will be a task to perform with a bare console only; not the most pleasant experience, indeed.

I would suggest to first try (again) to boot from usb.  Plug your usb flash, open the computer and go to BIOS settings; search for something that words like `boot sequence' or `disk config' or similar. You will know you are there if you see your flash drive; then figure out how to make it the fisrt device for boot. I haven't faced an Eeepc but I can't believe there is no such setting in the BIOS. You can also ask your supplier or the vendor for how to do this (this is an OS-unrelated question).

Then, if unsuccessful, to try remove the hard drive and attach it to a working system. Do this _only if the drive can easily be removed_ (for example you open a slot and see it) and after you have found in your laptop manual how this is exactly done; _you may damage the drive or your laptop if this is not done correctly_. If you can't or are afraid to do it it is better to try with BusyBox, or accept the loss of some files.

---

### Post by arnicainthemembrane on 2010-11-27
So... looking at my system from a live usb drive, I see two partitions which could contain root. /dev/sda6 and /dev/sda 7. apparently /dev/sda6 has the expected UUID. This makes it root?

---

