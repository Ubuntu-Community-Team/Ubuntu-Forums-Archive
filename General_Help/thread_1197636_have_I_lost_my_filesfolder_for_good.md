---
title: "have I lost my files/folder for good?"
date: 2009-06-26
forum: General Help
---

### Post by Ascenti0n on 2009-06-26
Hi all

I thought I'd ask here as Ubuntu forums always come through. I decided to try out the new Fedora 11 KDE on one of my hard drives, I have three on my machine. Unfortunately the installation isn't clear and as a result, my partition for storing data was LVM'ed. I don't know if the partition was formated or LVM is just a wrapper.

the data is on a partition called sdb6, and I can see it is still there via the F11 'live' disk, but can't do anything else.

Does anyone know if it is possible to restore my data, It contains the last few years worth of work, and 'not all' was backed up elsewhere.

Any help would be considered a life-saver.

---

### Post by rbc on 2009-06-26
Perhaps a silly question, but have you tried mounting using a live CD. And, for purposes of trying to recover the data later, I would mount it read-only

---

### Post by Ascenti0n on 2009-06-26
Yes, I did try to mount using the Live cd, but TBH I didn't know how to mount an LVM'ed partition.

what's frustrating is that there was no warning that I could see that the partition was going to be converted to LVM, it was already formated EXT4, if I remember rightly, which I did within Ubuntu.

---

### Post by jimv on 2009-06-26
So you can still see your data from Fedora?  As in, it's still there, but you can't get it from Ubuntu?

---

### Post by Ascenti0n on 2009-06-26
I can simply see that the partition is still there via a grey graphic, but nothing else.

I think I saw advice somewhere that you could create an image of the partitions' data and copy it to a working partition, but I don't know how viable this is or indeed if it will help me in my situation.

---

### Post by jimv on 2009-06-26
I've never done this, but this should get the volume mounted in Uubntu:

[http://www.linuxquestions.org/questions/fedora-35/how-can-i-mount-lvm-partition-in-ubuntu-569507/](http://www.linuxquestions.org/questions/fedora-35/how-can-i-mount-lvm-partition-in-ubuntu-569507/)

---

### Post by Greyfox_75 on 2009-06-26
What kind of filesystem was on before F11 LVMed over it?  Do you know which partition it was /dev/sda1?  

First thing you should do is use a tool like dd_rescue to make a full copy of all of the data inside that partition.  With this backup you should be able to restore your data back onto the partition if your rescue attempts make things worse.

Second thing you should do is try and determine if F11 put a new filesystem on your partition. 

sudo apt-get install lvm2

Then follow this site [http://www.brandonhutchinson.com/Mounting_a_Linux_LVM_volume.html](http://www.brandonhutchinson.com/Mounting_a_Linux_LVM_volume.html)
but do not mount the system read/write (we don't want to overwrite your info). So change his last command from 

mount /dev/VolGroup01/LogVol00 /tmp/mnt
to
mount -o ro /dev/VolGroup01/LogVol00 /tmp/mnt

Check if /tmp/mnt is empty or has your old files.  If it is empty data loss is almost certain. If it errors out and says no filesystem you might be okay.

If there is no new filesystem you could try using the backup superblock from the old filesystem and trying to repair from there.

fsck -b 32768 /dev/sda2

Anything beyond this is beyond me.  Look for some rescue tools and see if you can get in touch with their developers since they will know much more about these things.

---

### Post by Ascenti0n on 2009-06-26
I tried following examples, but failed at 2nd command:

```

sudo modprobe dm-mod

```

system returned:
```
FATAL: Module dm_mod not found.
```

---

### Post by jimv on 2009-06-26
> **Ascenti0n said:**
> I tried following examples, but failed at 2nd command:

```

sudo modprobe dm-mod

```

system returned:
```
FATAL: Module dm_mod not found.
```

I notice that module is not on my system either.  Perhaps skip that step and try the next one.

---

