---
title: "partition in 9.04"
date: 2009-10-28
forum: General Help
---

### Post by istor on 2009-10-28
Hello there! i am generaly a new user around here. i installed 9.04 in my main disk drive and now i want to make an extra partition in order to put my data in. 

How can i do it? am i going to lose any data? any link to read?

---

### Post by Mighty_Joe on 2009-10-28
[GParted]("http://gparted.sourceforge.net/") can resize partitions. The partitions in question cannot be mounted when you work on them. GParted provides a bootable CD or you can use the Ubuntu Live CD, where GParted is in the Admin menu as the "Partition Editor". 
Of course, you should always back up your data before performing any partition operation.

---

### Post by phillw on 2009-10-28
> **istor said:**
> Hello there! i am generaly a new user around here. i installed 9.04 in my main disk drive and now i want to make an extra partition in order to put my data in. 

How can i do it? am i going to lose any data? any link to read?

Welcome to the forums !!

There's an excellent how-to here ...  [http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

I like how-to's with screen-shots :D

There are a few more resources I use listed here ..  [http://www.vpolink.com/showthread.php?t=2756](http://www.vpolink.com/showthread.php?t=2756)

Regards,

Phill.

---

### Post by Giblet5 on 2009-10-28
The "usual" way of handling this is to mount an extra partition on /home after copying everything to the new partition.

This should be an ext2, ext3, or ext4 filesystem or you will be sorry... You were warned.

Let's say you just added /dev/sdb1, a 2TB ext3 partition. Here is how you would format that partition, copy the files, and make the mount automatic:

```
sudo bash ## This is VERY dangerous, so enter commands exactly
mkfs /dev/sdb1 # format the new partition
mount /dev/sdb1 /mnt -text # mount the new partition as /mnt
cd /home
tar cpf - . | (cd /mnt;tar xpf -) # copy everything
exit
```

Verify that the copy succeeded and that all timestamps and file permissions match between /home file structure and /mnt file structure. If tar didn't spew errors left and right, it succeeded.

Now log off.

Flip to the text console via CtrlAltF1 and log in.

```
sudo unmount /mnt
sudo rm -fr /home/*
mount /dev/sdb1 /home -text
exit
```

Flip back to the GUI via CtrlAltF7 and log in.

Bring up a terminal window and enter ```
sudo gedit /etc/fstab
```

Scroll to the bottom and add a new entry:
```
## Mount /home filesystem
/dev/sdb1  /home  ext**[COLOR="DarkRed"]N[/COLOR]**  noatime,errors=remount-ro  0  1
```

where **[COLOR="DarkRed"]N[/COLOR]** is 2, 3, or 4, depending on the fs type you chose.

Save it. You're all done.

---

