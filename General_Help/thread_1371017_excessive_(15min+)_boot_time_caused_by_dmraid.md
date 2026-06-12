---
title: "excessive (15min+) boot time caused by dmraid"
date: 2010-01-02
forum: General Help
---

### Post by skralljt on 2010-01-02
I have a truecrypt partition on an nvidia fakeraid raid0.  Therefore there is no data recognizeable to ubuntu's kernel on startup and I think it is causing a big slowdown for me every time I boot up, which takes over ten minutes every time.  Attached are bootchart results.
What I would like to do is know how to remove dmraid from the startup process.  I can't find any scripts in /etc/rc*.d and all of the information I can find on these forums is about how to enable dmraid on boot, not disable it.  Manually using dmraid takes nearly no time at all, which is what I did before this kernel upgrade since ubuntu didn't put dmraid in the startup process.  I can't see why it takes dmraid ten minutes to detect raid devices now!  The only clue I can see is that in the startup process with the splash screen disabled it talks about examining inodes on both drives in the array and then goes on to spit out stuff about raid 0, raid1, raid2, raid3, raid4 and on and on so it seems like it is loading raid arrays that don't exist and never have.  
If any bootchart gurus have any advice, please feel free to throw me a bone, I am in fear of restarting!
edit: for some reason ubuntuforums shrank my images so that they are unreadable by anybody except those with a large projector.  Therefore I have hosted one bootchart that is illustrative of my problems at imageshack:[http://yfrog.com/jaamd64karmic200912283p]("http://yfrog.com/jaamd64karmic200912283p")

---

### Post by skralljt on 2010-01-09
For anybody who found this because they have the same problem: i solved my excessive boot time issues (booting now in under a minute) by disabling dmraid at boot.  This is done by adding nodmraid to the kernel options. to illustrate this, following is the grub entry for my latest kernel:

```
title		Ubuntu 9.10, kernel 2.6.31-17-generic
		root (hd0,3)
uuid		670b0322-2c20-4792-8634-a2ad09eec05a
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=670b0322-2c20-4792-8634-a2ad09eec05a ro nodmraid
initrd		/boot/initrd.img-2.6.31-17-generic
```

The root hd0,3 part is so that another linux installation, slitaz, can read my grub file.  ubuntu detects slitaz and copies kernel and boot information but slitaz does not so it is necessary to use slitaz as the primary boot partition and use its version of grub. everything else works fine for ubuntu too, you can omit the root hd0,3 part because ubuntu uses a different method of identifying disks and partitions.

---

