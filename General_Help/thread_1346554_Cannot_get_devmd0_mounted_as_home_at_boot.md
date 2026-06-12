---
title: "Cannot get /dev/md0 mounted as /home at boot"
date: 2009-12-05
forum: General Help
---

### Post by SuperScottishHero on 2009-12-05
I've searched through the forums and nothing seems to help with this. It may also be that the kernel upgrade makes a difference.

I had ubuntu home edition, added the mdadm package and moved my /home to a software raid which was created with the palimpset disk utility. Subseuently the auto package manager upgraded the kernel.

Booting to 2.6.31-15 gives me ESC to go to a shell where:

mdadm --assemble /dev/md0 /dev/sda3 /dev/sdb3 
mount /dev/md0 /home

lets me boot

but the 31-16 kernel gives me initramfs

I've tried various thigns from the forums but nothing helps!

How can I get my /home automatically?

---

### Post by amauk on 2009-12-05
have you updated /etc/fstab ?

(assuming the raid is formatted ext4, if not amend to suit)

```
/dev/md0  /home  ext4  defaults  0  2
```

---

### Post by SuperScottishHero on 2009-12-05
Yes, /etc/fstab has:

/dev/md0     /home    ext3     nodev,nos uid                    0  2

and 
/etc/mdadm/mdadm.conf has:

ARRAY /dev/md/RAID data level=raid1 metadata=1.2 num-devices=2 UUID=06b5fbbd:7a8
1e036:13459d15:f8b3a4a3 name=:RAID data

but the boot tells me that it cannot find /dev/md0 to be able to mount /home from there and it falls into the shell. However, the commands I said before work fine in that shell.

---

### Post by amauk on 2009-12-05
try this
make a backup of mdadm.conf
change to read
```
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=06b5fbbd:7a81e036:13459d15:f8b3a4a3
```

*edit*
> /dev/md0 /home ext3 nodev,[COLOR="Red"]nos uid[/COLOR] 0 2
is that space there in your fstab, or just a typo on your post?

---

### Post by SuperScottishHero on 2009-12-05
> **amauk said:**
> try this
make a backup of mdadm.conf
change to read
```
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=06b5fbbd:7a81e036:13459d15:f8b3a4a3 
```

Thanks, this worked... but WHY? I thought I could use the output from mdadm --detail --scan directly?

> 
is that space there in your fstab, or just a typo on your post?It was a typo, thanks.

---

### Post by amauk on 2009-12-05
> **SuperScottishHero said:**
> Thanks, this worked... but WHY?I don't really know,
but it looked wrong, so I re-wrote the line based on my own raid5 array

> **SuperScottishHero said:**
> I thought I could use the output from[FONT=monospace] [/FONT]mdadm --detail --scan directly?Yes, you should be able to.
does ```
mdadm --detail --scan
``` still give you the original line?

---

