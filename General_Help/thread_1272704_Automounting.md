---
title: "Automounting?"
date: 2009-09-22
forum: General Help
---

### Post by NFblaze on 2009-09-22
Hi, its been a while since I've had any real problems (maybe one or two minor), but I've stumbled onto one that is now plaguing me.

Its a problem with automounting, when I plug in my Toshiba 500GB hard drive it will be found my gnome/ubuntu and automount as a FUSE device no questions asked.

Let's say I'm watchin a movie in Totem and it gets disconnected. Sometimes, it will not reconnect the drive. In fact the drive isnt recognized by the *mount* command. I would have to restart the computer for it to reconnect.

 This generally happens also, if I quickly remove the mini-usb plug and re-attach in 1-to-2 quick successions.

Although, if I do an *lsof* I can see that the kernel recognizes it. 

So, it leads me to believe something related to some service or program. On, the contrary tho with my other OS I can unsafely remove and mount over and over. So does anybody have an idea of the programs or services or in general the process used by ubuntu to automount hard drives so that I can attempt to work around it. Thx.

---

### Post by openfly on 2009-09-22
At the end of the day... everything uses mount.

man mount.

---

### Post by P4man on 2009-09-22
whether you do it quickly or slowly, if you don't do it *safely*, that is, unmounting the device first, you'll run in to trouble. Am I right guessing its an ntfs volume? If you disconnect the drive without unmounting it first, it will be flagged as dirty, and ubuntu will not mount it until its checked. And the only safe way to check it, is booting windows.

---

### Post by NFblaze on 2009-09-22
Yes, it is an ntfs mount. Though, this is not necessarily only when doing rapid unsafe mounting. This also happens if it disconnects in the middle of a movie I'm watching on Totem. I really would love to know the process it goes about mounting it. Thanks, for your answers tho.

---

### Post by whitethorn on 2009-09-22
I usually use

```
sudo ntfs-3g /dev/sdb1 /media/usb
```

Where I have already created a /media/usb folder and dev/sdb1 is the partition on my usb drive.  For ntfs drives you use the ntfs-3g driver.  See if that works for you.

---

### Post by NFblaze on 2009-09-22
> **whitethorn said:**
> I usually use

```
sudo ntfs-3g /dev/sdb1 /media/usb
```

Where I have already created a /media/usb folder and dev/sdb1 is the partition on my usb drive.  For ntfs drives you use the ntfs-3g driver.  See if that works for you.

That's nice, but the problem is that gnome or ubuntu uses something to automount the hard drive. Which if hot disconnected disables the system or something from being able to even read the device properly, hence why I wrote the *mount* command doesnt detect the filesystem on the hard drive, although I can see that it has  been recognized thru *lsof*. Yes, this is even after using the force switch btw.

---

