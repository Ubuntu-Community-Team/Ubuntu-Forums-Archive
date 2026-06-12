---
title: "About to give up on main ubuntu boot...please help"
date: 2010-06-30
forum: General Help
---

### Post by acegik on 2010-06-30
I am about to give up on my main ubuntu boot. 
Here is the story... I was using my computer normally when all of the sudden it froze, so I forced off. I rebooted and couldn't load ubuntu (It gave me some error that I don't remember! sorry!!) I re-booted it again and nothing...I researched the error and followed some instructions through terminal in live CD, I reboot it and got a screen with different kernell boots, I tried all of them some did nothing, in others I got error 18: "Selected cylinder exceeds maximum supported by BIOS" then I tried to modify my BIOS setting up the HDD to manual, it didn't work. From there I tried to restore GRUB. I tried reinstalling through live CD but at the time of install it hangs on "removing conflicting operating systems." Last thing I did is to run: 
fdisk -l 
cat /*/*etc/fstab
e2fsck -fyv /dev/sda1 but I interrupted this last one because I though it was deleting my files.

My HDD has two main partitions. The bigger one (sda1) belongs to ubuntu (first OS installed on this computer) on the second (sda2) I installed windows 7 after not being able to fix ubuntu and trying to recover my files. I also installed the lattes ubuntu version on this partition to acces my files. Both attempt resulted on failure. 
I am able to navigate through sda1 but I don't see my older document folder.
At this point I just want to recover my old documents and restore my partition

Please Help!!

---

### Post by cariboo on 2010-06-30
Try:

```
sudo fsck -a /dev/sda
```

When you are running from the Live CD, the -a stands for automatically fix.

If your other attempt at installation failed, you may be looking at a bad hard drive. I would suggest you go to the hard drive manufacturers web site and download their diagnostic tools and use them.

---

### Post by acegik on 2010-07-01
This is what I got when running the code:

> ubuntu@ubuntu:~$ sudo fsck -a /dev/sda
fsck from util-linux-ng 2.17.2
fsck.ext2: Device or resource busy while trying to open /dev/sda
Filesystem mounted or opened exclusively by another program?
ubuntu@ubuntu:~$ 
 
Any suggestion?

---

### Post by acegik on 2010-07-01
I added 1 at the end of sda and ran it again:
> ubuntu@ubuntu:~$ sudo fsck -a /dev/sda1
fsck from util-linux-ng 2.17.2
/dev/sda1 contains a file system with errors, check forced.
/dev/sda1: Missing '..' in directory inode 411838.


/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
	(i.e., without -a or -p options)


---

### Post by oldfred on 2010-07-01
Try this:

Must be unmounted:
Try "e2fsck -f /dev/sdb2". Ordinarily, fsck skips most of the check if the filesystem is marked as clean. The "-f" option to e2fsck (note: e2fsck, not fsck) forces a full check even if the filesystem is marked as clean.

From liveCD so everything is unmounted
sudo e2fsck -C0 -p -f -v /dev/sdb1
if errors:
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by acegik on 2010-07-05
Thank you, it worked! although I will probably have to reinstall I was able to recover my files. Thanks for your help again!:D

---

