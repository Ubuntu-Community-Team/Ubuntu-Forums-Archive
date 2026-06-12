---
title: "Error 15 Can't Boot"
date: 2009-10-03
forum: General Help
---

### Post by thecow on 2009-10-03
I installed Karmic beta, I followed this guide:
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

However when I went to restart it decided to no longer boot.  It doesn't go into grub at all it merely gives me an "Error 15" message and that is that.

So I am presently on a Live CD version of Karmic.  I have my hard drive mounted so I can edit files, however I am not sure what to edit here.

According to that wiki:
"    Now you need to edit the /etc/default/grub file to fit your system 

$ nano /etc/default/grub
"

However I see nothing that needs to be changed there (Ill post it if need be but theres little information in there)


Next the wiki says to run update-grub, I get this:
```
root@ubuntu:/# update-grub
grub-probe: error: cannot find a device for /.

```


Next it tells me to run grub-install /dev/sda
```
root@ubuntu:/# update-grub
grub-probe: error: cannot find a device for /.

```


So I have no idea how to fix this, anyone have any thoughts?

---

### Post by blueridgedog on 2009-10-03
I suggest you manually try and install grub.  Here are the standard instructions:

Bootup a live cd, open a terminal and do the following.
```

sudo grub
```

This will result in a "grub>" prompt. At grub>. enter these commands
```

find /boot/grub/stage1
```

This will return a location. If you have more than one, select the installation that you want to use as the source for the new mbr.

Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)

```
root (hd?,?)
```

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr

```
setup (hd0)
```

Note, if you want to put the new mbr in another hard drive, you will need to adjust it accordingly.

Finally exit the grub shell
```

quit
```

---

### Post by TheGreenFox on 2009-10-03
Use Super Grub Disk that thing works magic. Just burn to CD bootup and run the linux auto fix. It has solved 90% of my grub errors.

[http://www.supergrubdisk.org/index.php?pid=5](http://www.supergrubdisk.org/index.php?pid=5)

---

### Post by thecow on 2009-10-03
Well Im not sure I mounted the boot part as listed on fdisk properly:

```
ubuntu@ubuntu:/mnt$ sudo fdisk -l

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5c625c62

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11661    93666951   83  Linux
/dev/sda2           11662       12159     4000185    5  Extended
/dev/sda5           11662       12159     4000153+  82  Linux swap / Solaris

```

I mounted /dev/sda1 in /mnt.  On a wiki I read that sometimes there is a seperate boot partition so people need to mount that to /mnt/boot, I did not do this.



As for your comments:
```
grub> find /boot/grub/stage1

Error 15: File not found

```


I should mention that this all stopped working after I tried to install grub2 as based on the wiki above, I am running this version of grub now:
```

# grub-install -v
grub-install (GNU GRUB 1.97~beta3)

```

---

### Post by thecow on 2009-10-03
> **TheGreenFox said:**
> Use Super Grub Disk that thing works magic. Just burn to CD bootup and run the linux auto fix. It has solved 90% of my grub errors.

[http://www.supergrubdisk.org/index.php?pid=5](http://www.supergrubdisk.org/index.php?pid=5)
I might try that later if nothing else works but first Id like to take care of this in Ubuntu

---

### Post by thecow on 2009-10-03
My device.map has only this one line in it:
"(hd0)   /dev/sda"

I am not sure if this is correct, is there some way to verify that this information is good?

---

### Post by blueridgedog on 2009-10-04
> **thecow said:**
> 
I should mention that this all stopped working after I tried to install grub2 as based on the wiki above


I read the wiki.  Did you have a working karmic system prior to the attempt to install grub2?

Since you have grub 1.97, it is hard to tell if you were installing karmic, or just grub.

Do you want to 2.0 working or install the old grub?  Have you tried the recover steps: [https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD) ?

---

