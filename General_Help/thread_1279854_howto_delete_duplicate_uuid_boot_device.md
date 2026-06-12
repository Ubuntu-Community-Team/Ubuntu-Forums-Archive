---
title: "howto delete duplicate uuid boot device"
date: 2009-10-01
forum: General Help
---

### Post by jlm33990 on 2009-10-01
my 9.04 system has two disks with same uuid. 

here's what happened..
shutdown -h
cloned primary disk to secondary disk using ghost - same geometry, model, etc 
test boot from cloned disk fails (now I know ghost does not support ext3)
now primary will not boot (cannot find init)
boot from cd
mount & edit menu.lst 
changed root=uuid=... to root=/dev/sda1
back up
 
root@butu1:/boot/grub# blkid
/dev/sda1: UUID="b0ad3a30-9342-4240-b774-0c45e590fbc0" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="cbb6b76a-329b-425e-8714-f5835e996304" 
/dev/sdb1: UUID="b0ad3a30-9342-4240-b774-0c45e590fbc0" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: TYPE="swap" 
 
you can see that sda & sdb have same uuid which probably caused the boot problem.
not sure how that happened..maybe me changing the bios to test boot the cloned disk??? more likely the ghost clone. not sure if it's a bug or me doing something wrong. I'm fairly new to ubuntu.
 
is there a command to remove from the sdb disk from the blkid list show above so I can go back to the uuid method of booting?
 
also, since the ghost clone is probably the root of the problem. please tell me the best way to make a bootable backup on the secondary disk. thanks...

---

### Post by StuartN on 2009-10-01
tune2fs will let you change the UUID. uuidgen will create a new UUID for tune2fs.

---

### Post by cdenley on 2009-10-01
```

sudo tune2fs -U random /dev/sdb1

```

---

### Post by jlm33990 on 2009-10-01
any idea why this didn't work??
 
root@butu1:/boot/grub# blkid
/dev/sda1: UUID="b0ad3a30-9342-4240-b774-0c45e590fbc0" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="cbb6b76a-329b-425e-8714-f5835e996304" 
/dev/sdb1: UUID="b0ad3a30-9342-4240-b774-0c45e590fbc0" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: TYPE="swap" 
root@butu1:/boot/grub# tune2fs -U clear /dev/sdb1
tune2fs 1.41.4 (27-Jan-2009)
root@butu1:/boot/grub# blkid
/dev/sda1: UUID="b0ad3a30-9342-4240-b774-0c45e590fbc0" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="cbb6b76a-329b-425e-8714-f5835e996304" 
/dev/sdb1: UUID="b0ad3a30-9342-4240-b774-0c45e590fbc0" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: TYPE="swap" 
root@butu1:/boot/grub#

---

### Post by arrange on 2009-10-01
Don't use *blkid*, use ```
blkid -c /dev/null
```instead.

---

### Post by jlm33990 on 2009-10-01
blkid -c /dev/null - did nothing - i'm confused by your reply
 
my question was why tune2fs -U clear /dev/sdb1 did not clear the uuid - see my last post

---

### Post by arrange on 2009-10-01
I supposed you were still *root*... so then run ```
sudo blkid -c /dev/null
```I guess *blkid* was using the old cache, that's why I'm suggesting using the latter command to clear the cache and renew it from the scratch so that you can see the actual values.

---

### Post by jlm33990 on 2009-10-01
my mistake...you supposed correctly
thanks

---

### Post by Jerubaal on 2009-10-17
Just what I needed to find - thanks!

Ubuntu kept booting into a random clone & not necessarily the current version!

Now to find out how to change the drive label, cos that got cloned, too.

---

