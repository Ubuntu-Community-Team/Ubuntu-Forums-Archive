---
title: "USB HDD random disconnects?"
date: 2010-12-09
forum: General Help
---

### Post by dannyboy79 on 2010-12-09
Not sure if my external usb hard drive is dieing or what the deal is. I noticed this weird problem after I upgraded the kernel to 2.6.32-21-generic. It could be a coincidence that it starting occurring after i upgraded (thru synaptic) the kernel or maybe it's dieing. Looking for feedback from others. Here's the output from running
```
dmesg
```
[http://pastebin.com/0Kn5ht7T]("http://pastebin.com/0Kn5ht7T")
What's more weird is that it also keeps changing device locations. WHen I first start the computer it's something like /dev/sde1. But when it disconnects and I remount it, i have to mount it as /dev/sdf1. well then the next time it's /dev/sdg1. Now you can see by my pastebin above that sdg1 is now not working. Here's the output from the mount command
```
mount
```
/dev/sde1 on /media/500gb type ext3 (rw,relatime)
nfsd on /proc/fs/nfsd type nfsd (rw)
/dev/sdg1 on /media/500gb type ext3 (rw,relatime)
very confused why the mount results are different for the sde1 and sdg1. I do share the drive out to other computers with NFS.
here's my fstab
[http://pastebin.com/eY14TLGK]("http://pastebin.com/eY14TLGK")
more weird is that when i issue sudo fdisk -l it shows it as /dev/sdf1

any thoughts would be much appreciated as this problem is very confusing to me.

---

### Post by cylo on 2010-12-09
I have the same issue.  3 days ago upgraded to the latest 10.10 LTS.  I have 3 external usb drives.  One will always retain its /dev/sdc1 assignment.  Sometimes the second will retain its /dev/sdd1 assignment.  But the third one is chasing between sde1, sdf1, and is now up to sdg1.  No reboots between changes.  The /media folder shows the UUID of all these attempts.  And System Monitor shows all the previous sdx# assignments for the same drive.  It looks like I have 6 or 7 drives mounted instead of the actual three.  

When I do a 'sudo blkid" the migrating drive does not have a Sec_Type reported, the other stationary drives do.  Could that be a clue?

---

### Post by WorMzy on 2010-12-09
10.10 isn't a LTS, 10.04 is.

@OP, it's unrelated, but your fat32 partition's entry in fstab has a 1 under pass column. That's not good, change it to a 2 or a 0; only the root (/) partition should have a 1.

About the disconnecting drive, the symptoms, to me, suggest a hardware failure, but the dmesg output suggests minor filesystem corruption. It's possible that the filesystem has corrupted due to the repeated unsafe disconnects, so it'd probably be a waste of time trying to fix that until the hardware issue is resolved. Unfortunately, I can't really offer any advice regarding this, as I have no experience with USB hard drives. All I can suggest is that you check the cable is secure and undamaged, and that the hard drive itself is kept of a flat, stable surface, and away from magnets, strong sunlight, and liquids.

Oh, and lack of sec_type isn't anything to worry about. sec_type is just a secondary type that the filesystem can be mounted as. Ext3 can be mounted as ext2, because ext3 is just ext2 with a journal. I believe ext4 is backwards-compatible with ext3 now too.

---

### Post by cylo on 2010-12-11
I'm pretty sure mine is not related to hardware failure of the drive, I have three of these drives, all new, connected.  And it's always the 'third' drive to connect which is randomly changing.  I thought it may be the usb ports on the pc, so I disabled the motherboard usb ports and purchased add-in pcmcia usb cards. Still the random drops.  I suppose it could be the cables, also new.  I'll try those next.....

---

### Post by dannyboy79 on 2010-12-11
have you tried going to a different kernel? that's what I am going to be trying to today. im at 2.6.32-21-generic and am going to go back to 2.6.32-19-generic. I also just noticed that this is an older kernel. I must not have upgraded this server in a long time. My other Ubuntu box is running 2.6.32-24-generic, both are running 10.04.

---

