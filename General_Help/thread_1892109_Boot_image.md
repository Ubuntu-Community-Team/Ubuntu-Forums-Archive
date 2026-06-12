---
title: "Boot image"
date: 2011-12-07
forum: General Help
---

### Post by tr1ck on 2011-12-07
Hey guys,

I'm trying to update a couple of files on a boot image that we use to  run a low form of linux on some boards for testing. We basically install  the image to create a bootable sdcard with this low form of linux.
Anyway I have a final.image.dd file that I usually create the sdcards  from, but i need to edit the interfaces and replace a file from inside  the .dd image.
Any pointers on how this could be done?

Thank you.

P.S. I'm using Ubuntu on the machine I'm doing all of this on.

---

### Post by matt_symes on 2011-12-07
Hi

Can you mount it as a loop back device ? Try using the  *-o loop *when mounting it.

Kind regards

---

### Post by tr1ck on 2011-12-07
i did a # mount /dev/sdb1 -o loop 
and it gave me no error.

---

### Post by tr1ck on 2011-12-07
root@ubuntu:/home/alex/Desktop/Fortress Tech CIP# parted Fortress-Tech.final.image.dd unit B print
Model:  (file)
Disk /home/alex/Desktop/Fortress Tech CIP/Fortress-Tech.final.image.dd: 2090860544B
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start     End         Size        Type     File system  Flags
 1      16384B    1572863B    1556480B    primary
 2      1572864B  2621439B    1048576B    primary  ext2
 3      4980736B  287047679B  282066944B  primary  ext3

root@ubuntu:/home/alex/Desktop/Fortress Tech CIP# sudo mount -o loop,offset=1572864B Fortress-Tech.final.image.dd /tmp/fti
mount: invalid offset '1572864B' specified
root@ubuntu:/home/alex/Desktop/Fortress Tech CIP#

---

### Post by matt_symes on 2011-12-07
Hi

Try these commands

```

sudo mkdir /mnt/mountpt
```

You may have to change the permissions of the mount point.

```
sudo mount -o loop,offset=1572864 Fortress-Tech.final.image.dd /mnt/mountpt
```

Notice there is no B in the offset and it is mounted to mountpt in /mnt. 

When finshed

```
sudo umount /mnt/mountpt
```

Kind regards

---

### Post by tr1ck on 2011-12-07
i eventually got it, thanks though :)

---

### Post by matt_symes on 2011-12-07
Hi

> **tr1ck said:**
> i eventually got it, thanks though :)

Excellent ! :P 

Can you mark this thread as solved please, using the thread tools at the top of the page.

Kind regards

---

