---
title: "ext3 partition fail? um... no?"
date: 2009-10-28
forum: General Help
---

### Post by Bölvaður on 2009-10-28
Im not sure where to turn.
I was middle of doing a help request when the partition suddenly mounted and everything became as cool as an icelolly.

[SIZE="5"]&#8594; &#8594; Does ubuntu check partitions in the background after declining the auto check at startup? &#8592; &#8592;[/SIZE]

From what I was writing in that request.



Story:

I boot up the computer in a hurry and disk check for some partition popped up. I pressed ESC to stop it.
I did not write anything to that partition, only read.

The same thing the next time I turned on the computer.
I only read data this time also.

The third time I did not press esc but it stopped very early on in the disk check. And the partition did not seem to mount even though it is in fstab.

The fourth time I turned on the computer it still didnt mount and it failed again doing the diskcheck at startup.
So I did the check from gparted. This is what I got from it:

```
GParted 0.4.5

Libparted 1.8.8.1.159-1e0e

Check and repair file system (ext3) on /dev/sda3  00:00:01    ( ERROR )
    	
calibrate /dev/sda3  00:00:01    ( SUCCESS )
    	
path: /dev/sda3
start: 101852100
end: 976768064
size: 874915965 (417.19 GiB)
check file system on /dev/sda3 for errors and (if possible) fix them  00:00:00    ( ERROR )
    	
e2fsck -f -y -v /dev/sda3
    	
Filesystem mounted or opened exclusively by another program?
e2fsck 1.41.9 (22-Aug-2009)
e2fsck: [_B]Device or resource busy while trying to open /dev/sda3[/B] _
========================================
```

This also:
```
$ sudo mount -a 
mount: /dev/sda3 already mounted or /data busy

```

The disk is in good condition, all the other partitions on it works. There is no process that looks like it is blocking... **waiit.. waiiit something is going on!** The partition is mounted again. -.- :-\"=D> there must have been something blocking the check... like another check... umm.. helvítis?

---

### Post by hal10000 on 2009-10-28
you can not fsck the partition while it is mounted, you first have to unmount it. Close all filemanagers and other apps which are currently accessing this partition and then do:
```
sudo umount /dev/sda3
sudo fsck.ext3 -f /dev/sda3
```

If it is your sytem-partition, then you have do do this on your ubuntu live-cd.

---

### Post by Bölvaður on 2009-10-29
I am terribly sorry but you must have fallen victim to the same thing as the mod that moved this thread. This is not a support thread.
What I said is this was going to be one, when all of a sudden the partition mounted an everything was ok. 

And the problems I was having forcing the check is most likely due to the check was being done in the background. I was only asking if that is the way it is done now, as I've never seen this before in any other distros.

---

