---
title: "no swap"
date: 2009-10-25
forum: General Help
---

### Post by fishbulb1022 on 2009-10-25
I had multiple partitions installed with different versions of ubuntu on them, each with its own swap. I was changing the partitions sizes to get more space on one of them and I figured it was a waste of space to have all the swaps, so I deleted all but one. Now my main partition does not recognize a swap partition at all (or at least conky doesn't see it). Do I just need to create another swap partition and place it directly after the main partition?

---

### Post by SPr on 2009-10-25
```

su
blkid |grep swap
cp /etc/fstab /etc/fstab.25.10.09
nano /etc/fstab

```
edit /etc/fstab so that the line with type "swap" has the data obtained from "blkid|grep swap".

If you completely mess it up remember that the third line of code created a copy.

---

### Post by fishbulb1022 on 2009-10-25
how exactly do I edit that line? I've used the terminal before, but I definitely wouldn't say I really know what I'm doing yet, so the more specific and basic you can be the better. Thanks for the help.

---

### Post by SPr on 2009-10-25
Have you run those commands yet? The last line invokes the nano text editor. If you wish change it to
```

gedit /etc/fstab

```

---

### Post by P4man on 2009-10-25
you need root privildges to edit that file, so that would be
```

**gksu** gedit /etc/fstab
```

edit. you used "su" in your command list. that wont work on ubuntu. ```
sudo su
``` should work instead

---

### Post by SPr on 2009-10-25
> **P4man said:**
> you need root privildges to edit that file, so that would be
```

**gksu** gedit /etc/fstab
```

No. If you read my first post I used "su" to get root permission. Changing to gedit:
```

su
blkid |grep swap
cp /etc/fstab /etc/fstab.25.10.09
gedit /etc/fstab

```

so strictly I should have added exit.
```

su
blkid |grep swap
cp /etc/fstab /etc/fstab.25.10.09
gedit /etc/fstab
exit

```
Woops. Just seen your edit! It must have changed since I used Ubuntu. Why should su have to be called with sudo? Can only root gain root privileges?
```

sudo blkid |grep swap
sudo cp /etc/fstab /etc/fstab.25.10.09
gksudo gedit /etc/fstab

```

---

### Post by P4man on 2009-10-25
root account is locked in ubuntu. Hence "su" doesnt work. You must have changed that manually. More info here:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by SPr on 2009-10-25
I realise root is locked but sudo su seems counter-intuitive.

For the OP: Have you fixed this yet? If you wish you can post the output of
```

sudo blkid|grep swap

```
and
```

cat /etc/fstab

```
for someone to do it for you if you're not sure.

---

### Post by fishbulb1022 on 2009-10-25
Thanks for all of your help, I ran the commands, here's the output: 

```
/dev/sda5: TYPE="swap" UUID="97671b4d-f885-4f96-a010-14fad7884337"
```

```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda11 during installation
UUID=a99e6a8a-cb67-4a9c-b6da-e2b8acf6c03a /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda12 during installation
UUID=37375a3c-5670-43f5-b146-afce85237a84 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```


I'm assuming I should be replacing UUID=37375a3c-5670-43f5-b146-afce85237a84 with UUID="97671b4d-f885-4f96-a010-14fad7884337, however, before I screw anything up, can someone confirm that t=I am correct?

Thank you again for the help.

---

### Post by P4man on 2009-10-25
Yep that should do it.
To edit fstab, run

```
gksu gedit /etc/fstab
```
(gksu being short for gksudo)

save the changes and reboot.

---

### Post by fishbulb1022 on 2009-10-25
Ok, I pasted the new line in, but I think I must have done something wrong, because its still not recognizing a swap partition. This is what the file looks like now

```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda11 during installation
UUID=a99e6a8a-cb67-4a9c-b6da-e2b8acf6c03a /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda12 during installation
UUID="97671b4d-f885-4f96-a010-14fad7884337 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

---

### Post by egalvan on 2009-10-25
> **fishbulb1022 said:**
> Ok, I pasted the new line in, but I think **I must have done something wrong,** because its still not recognizing a swap partition.
 This is what the file looks like now

```
# /etc/fstab: static file system information.
...
# swap was on /dev/sda12 during installation
UUID=[COLOR="Red"]"[/COLOR]97671b4d-f885-4f96-a010-14fad7884337 none        swap    sw       0       0
...
```

You have a wayward " at the beginning of the UUID itself.

Re-move it.
Re-save it.
Re-boot it.


BTW, I use

```
gksudo gedit "file name"
```

to edit system files.

gksudo is the way to execute Gnome GUI applications under root privileges.

---

### Post by fishbulb1022 on 2009-10-25
Thank you all very much for your help and patience, I've got it working again now.

---

### Post by P4man on 2009-10-26
> **egalvan said:**
> 

gksudo is the way to execute Gnome GUI applications under root privileges.

I figured gksu was just a short name of gksudo, but I just read the manpages:

> 
 gksu  is a frontend to su and gksudo is a frontend to sudo

..
Also notice that the library will decide if it should use su or sudo as
       backend  using the /apps/gksu/sudo-mode gconf key, if you call the gksu
       command..

Now Im not sure. Is there a difference?

---

