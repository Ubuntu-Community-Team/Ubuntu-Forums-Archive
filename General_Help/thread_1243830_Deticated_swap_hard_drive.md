---
title: "Deticated swap hard drive"
date: 2009-08-18
forum: General Help
---

### Post by conradin on 2009-08-18
Hi all, 
I have heard, that swap space over time wears out a hard drive. whether anyone agrees or not is irrelevant. What I have is several hard drives to spare. I have formated them with the linux-swap file-system. Now, how should I go about making my computer use this swap space?  I am suspecting that it wont happen automatically. Do I just add an other spot in the /etc/fstab?
Heres what my fstab looks like currently:
```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=2a4237ac-a4f1-49f5-811f-4383ef37157c /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=3ee09ddc-92fb-4227-99a5-e4b9912f6fe2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto     rw,user,noauto,exec,utf8 0       0

```

the new swap hard drive is at /dev/sdc1

---

### Post by michy99 on 2009-08-18
Find out the UUID of /dev/sdc1.```
sudo blkid /dev/sdc1
```Replace the UUID in the swap line in fstab.

---

### Post by bodhi.zazen on 2009-08-18
Depending on your RAM you can turn swap off and mount /tmp and /var/log into ram.

There is no specific how to on this, see what some of the netbooks are doing :

[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

---

### Post by dcstar on 2009-08-19
> **conradin said:**
> Hi all, 
I have heard, that swap space over time wears out a hard drive. whether anyone agrees or not is irrelevant. What I have is several hard drives to spare. I have formated them with the linux-swap file-system. Now, how should I go about making my computer use this swap space?


```
man swapon
```

---

### Post by conradin on 2009-08-21
Thank you all! I will give it a try tonite and let you know how it goes. I appreciate the input!

---

### Post by conradin on 2009-08-25
I just tried: 
```

sudo blkid /dev/sdb1


```
created an alternate fstab entrie for swap using the sdb1 UUID, rebooted,
 then used the free command and got:
```

$ free
             total       used       free     shared    buffers     cached
Mem:       1017840     341536     676304          0      16068     175820
-/+ buffers/cache:     149648     868192
Swap:            0          0          0


```

I guess Ill try swapon next unless some one sees something I did wrong.

---

### Post by bodhi.zazen on 2009-08-25
Post the output of that command as well as your fstab entry.

---

