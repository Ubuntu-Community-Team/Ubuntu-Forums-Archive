---
title: "RAID not found at boot"
date: 2009-09-14
forum: General Help
---

### Post by skewray on 2009-09-14
I am trying to recover from a dmraid accident.  I ran the command out of curiosity and it blew up my mdadm raid.  Now I am trying to recover.

My computer has a raid-1 root partition and a regular /boot partition. The root partition is specified by UUID in the grub menu, and I have verified that it is correct with vol_id.  The problem is that every time I boot up, it can't find root and drops me into an initramfs shell.  If I then type in "mdadm --auto-detect" it immediately finds the raid-1 root partition, and then I can exit the shell and boot proceeds without a problem.

How do make the computer recognize the raid-1 partition without being told?  I tried reconfiguring kernel package, but that didn't help.

Thanks in advance,

Brian

---

### Post by tgrimley on 2009-09-14
Maybe try reconfiguring mdadm so it inserts itself at boot again?

---

### Post by skewray on 2009-09-14
I don't know how to reconfigure mdadm.  How do I do that?  During the boot process the machine has already recognized two other raid arrays.  It just doesn't find the one root wants.  Running 'mdadm --auto-detect' after boot does nothing.

Thanks!

Brian

---

### Post by tgrimley on 2009-09-14
> **skewray said:**
> I don't know how to reconfigure mdadm.  How do I do that?  During the boot process the machine has already recognized two other raid arrays.  It just doesn't find the one root wants.  Running 'mdadm --auto-detect' after boot does nothing.

Thanks!

Brian

I just meant dpkg-reconfigure, but to be honest if it's detecting some arrays but not others I doubt that will do much for you.

Can you paste the contents of your mdadm.conf and the output of the 'blkid' command maybe a 'dmesg | grep md' too??

---

### Post by skewray on 2009-09-15
> **tgrimley said:**
> I just meant dpkg-reconfigure, but to be honest if it's detecting some arrays but not others I doubt that will do much for you.

Can you paste the contents of your mdadm.conf and the output of the 'blkid' command maybe a 'dmesg | grep md' too??

Sure.  See attached.  Any clues?

Brian

---

### Post by tgrimley on 2009-09-15
You might want to add the ARRAY line to your mdadm.conf so it has an easier time assembling.  Looks like you have multiple arrays too so you'll definitely want to do this.

check out [http://linux.derkeiler.com/Mailing-Lists/Debian/2008-12/msg00281.html](http://linux.derkeiler.com/Mailing-Lists/Debian/2008-12/msg00281.html)

You want to add a line like 
ARRAY /dev/md0 level=raid5 num-devices=3 UUID=117232ce:f55876b7:9822568f:9ddc1a1a

which you can get like this
```
tgrimley@gutsy:~$ sudo mdadm --examine --scan /dev/sdd1
ARRAY /dev/md1 level=raid5 num-devices=3 UUID=30107048:0b2c1028:06467301:4adf355b

```

---

### Post by skewray on 2009-09-15
> **tgrimley said:**
> You might want to add the ARRAY line to your mdadm.conf so it has an easier time assembling.  Looks like you have multiple arrays too so you'll definitely want to do this.

check out [http://linux.derkeiler.com/Mailing-Lists/Debian/2008-12/msg00281.html](http://linux.derkeiler.com/Mailing-Lists/Debian/2008-12/msg00281.html)

You want to add a line like 
ARRAY /dev/md0 level=raid5 num-devices=3 UUID=117232ce:f55876b7:9822568f:9ddc1a1a

which you can get like this
```
tgrimley@gutsy:~$ sudo mdadm --examine --scan /dev/sdd1
ARRAY /dev/md1 level=raid5 num-devices=3 UUID=30107048:0b2c1028:06467301:4adf355b

```

If I run that mdadm command over all of my partitions, they are all different except the two that make up /dev/md2, the one causing all of the trouble.  I am not sure what that means, but it is now past my bedtime.

Brian

---

### Post by jverge on 2009-09-15
try giving the rootdelay=180 option in the kernel.  That worked for my server.  The default just wasn't enough time to find the / partition for some reason.

---

### Post by skewray on 2009-09-18
> **jverge said:**
> try giving the rootdelay=180 option in the kernel.  That worked for my server.  The default just wasn't enough time to find the / partition for some reason.

Doesn't help.  I don't think the problem is a speed issue.

Brian

---

