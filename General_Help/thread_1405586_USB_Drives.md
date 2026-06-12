---
title: "USB Drives"
date: 2010-02-12
forum: General Help
---

### Post by jlbprof on 2010-02-12
I have 2 USB NTFS drives that mount and work perfectly.

One mounts at /media/FreeAgentDrive and the other at
/media/FreeAgentDrive_

The order they are connected I believe is what decides what the mount point is.  So if they are brought online in a different order they would have the opposite names.

I would like them to have unique names and always mount in the same location regardless of how and when they are brought online.

Is this possible?

I tried using Palimsest, but it cannot change anything all is greyed out.

Thanx

Julian

---

### Post by spiderbatdad on 2010-02-12
possibly launch palimsest from your terminal as root?

I have never used the program but presumably it runs from the terminal when the program name is typed in. So try sudo palimsest

---

### Post by mechro on 2010-02-12
Try unmounting the partitions before using Palimpsest.

---

### Post by Luisnux on 2010-02-12
You may want to give unique names to each of those two drives.  For example I have a 160GB hard drive that I named 160GB (very original :)), and one that I names Lexar.  That way regardless of which one I plug in my system, I know which one I'm working with.  Hope this helps.:D

---

### Post by MooPi on 2010-02-12
I believe gparted would allow you to change the drives designation. Can be install via synaptic or apt-get.

---

### Post by mechro on 2010-02-12
By the way, if Palimpsest won't let you Label the partitions try here...

[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

---

### Post by spiderbatdad on 2010-02-12
so I was just trying the utility and I get no useful options either regardless of running the program as root or whether the file ystem is mounted.

You can use labels for the devices...the are a number of tutorials for that.

[http://blog.bodhizazen.net/linux/understanding-fstab-pdf-version/](http://blog.bodhizazen.net/linux/understanding-fstab-pdf-version/)

Not sure how you generate the menuentry for grub2...possibly the option is specified in /etc/default/grub...sorry I have tried technique.

---

### Post by ironclaw on 2010-02-13
The simplest solution is to use 'ntfslabel' to change the labels of the drives. I'm not sure if it's included in Ubuntu by default - it's in the 'ntfsprogs' package.

Unmount the ntfs drives first, then
```
sudo ntfslabel /dev/<device> <new label>
```
to change the label of /dev/<device> to <new label>.

The partition should then mount automatically in /media/<new label> when the USB drive is plugged in. As long as the 2 labels are unique, there shouldn't be any confusion.

---

