---
title: "Help on Recovery?"
date: 2010-09-28
forum: General Help
---

### Post by alphaamanitin on 2010-09-28
Hey guys.  

See this thread for an explanation of why I am doing a recovery, and to have a laugh:

[http://ubuntuforums.org/showthread.php?t=1583875](http://ubuntuforums.org/showthread.php?t=1583875)

Anyway, the short of it is I was following these steps:

Boot into liveCD, get console:

udo mkdir /mnt/repair 

sudo mount /dev/sdb1 /mnt/repair 

sudo chroot /mnt/repair su 

sudo apt-get update
sudo apt-get upgrade 
sudo  aptitude upgrade
sudo apt-get -f  install
sudo dpkg --configure -a
sudo apt-get upgrade


exit
sudo reboot

But when I try to use 'sudo chroot /mnt/repair su' I get "chroot: cannot run command '/bin/bash': No such file or directory"  What is up?

AlphaA

---

### Post by CharlesA on 2010-09-28
Are you using a different version of livecd? 32-bit for a 64-bit install, or vice verse?

I ran into that same problem.

---

### Post by coffeecat on 2010-09-28
I think chroot-ing is a bit more complicated. This is what I do.

First - get a root prompt. it's easier.

```
sudo su
```Then...

```
mount --bind /dev /mnt/repair/dev
mount --bind /dev/pts /mnt/repair/dev/pts
mount --bind /dev/shm /mnt/repair/dev/shm
cp -L /etc/resolv.conf /mnt/repair/etc/
chroot /mnt/repair
```Then do all your apt-gets and stuff, but without sudo because you have a root prompt in your chroot. And don't forget that resolv.conf line otherwise you won't be able to download stuff in the chroot.

Finally...

```
exit
```to exit the chroot environment, and 

```
exit
```to exit the root shell.

---

### Post by alphaamanitin on 2010-09-28
Hmm.  I am not sure about the version of the live CD.  I am still running 9.10 and the LiveCD version is 9.10.  However, I know that there will have been many updates to my 9.10 OS, could this be a problem?

To coffeecat:

Could you explain the first section of code after the sudo su?  I am not sure about it.

Thanks,

AlphaA

---

### Post by coffeecat on 2010-09-28
You need to mount /dev into your chroot environment otherwise it won't work - or so I believe. /dev/pts is pseudo-terminal slave and theoretically the terminal won't work without it. /dev/shm is a filesystem that keeps files in virtual memory. But, tbh, I've got used to including the /dev/pts and /dev/shm lines and they may not be necessary. This Gentoo documentation page:

[http://www.gentoo.org/doc/en/handbook/handbook-amd64.xml?full=1#book_part1_chap6](http://www.gentoo.org/doc/en/handbook/handbook-amd64.xml?full=1#book_part1_chap6)

...only mounts /dev, but it also mounts /proc. I used a chroot environment to netinstall Maverick on another partition last week and I didn't mount /proc, so you can probably get away with that. But at least you must mount /dev (I believe) and you must copy resolv.conf if you're going to be using networking in the chroot environment.

This Ubuntu page:

[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)

Only mounts /proc, so there you have it: complete agreement. :lol:

---

### Post by alphaamanitin on 2010-09-28
yeah, so I still get the same error when using chroot.  I think I am screwed.  Oh well.  I will see if I can recover data and reinstall unless you have more hints.

AlphaA

---

### Post by CharlesA on 2010-09-28
> **alphaamanitin said:**
> yeah, so I still get the same error when using chroot.  I think I am screwed.  Oh well.  I will see if I can recover data and reinstall unless you have more hints.

AlphaA

When you boot from the livecd, run this:

```
uname -a
```

If it says x86, it's 32-bit. If it says x86_64, then it's 64-bit.

If you are using a 32-bit livecd, you might need to use a 64-bit livecd to fix the problem.

---

### Post by alphaamanitin on 2010-09-28
Well, I know I installed 32 bit Ubuntu 9.10, so do I still need to do this Charles?  Would using a 64 bit disk help?  Or were you merely thinking that I may be using a wrong bit version livecd compared to what I had installed?  Either way I will do this tomorrow morning and report back.

Thanks guys.  I would really like to get it going if possible.  I did not have any luck opening the drive while in a liveCD environment to back up the data.  I have not tried it on a actual install of Ubuntu yet though and I would need to make one to do so.  

AlphaA

---

### Post by CharlesA on 2010-09-28
If the architechure of the install is different from the livecd you are trying to chroot into, it'll have problems. If both are 32-bit then it should have worked.

---

### Post by alphaamanitin on 2010-09-29
This is what uname -a give me as an output:

Linux ubuntu 2.6.31-14-generic #48-Ubuntu SMP Friday Oct 16 14:04:26 UTC 2009 i686 GNU/Linux

If I recall correctly i686 is 32 bit architecture yes?  Any ideas on why chroot won't work.  I still get the same error found in my original post.

AlphaA

---

### Post by CharlesA on 2010-09-29
So strange. Are you able to just mount the device and pull yer data off?

---

### Post by alphaamanitin on 2010-09-29
I don't appear to be able to.  I tried mounting it, but I am not sure I did it correctly.  blkid reveals that my ext3 partition is /dev/sdb1 and my swap partition is /dev/sdb2.  

sudo mount /dev/sdb1 does not work.  But I have not had to manual mounting without a GUI in quite a while.  Plugging the external HD in after the LiveCD has started up does nothing, and I have not been able to get it mounted.  I will try again and let you know.

AlphaA

---

### Post by CharlesA on 2010-09-29
Try it on a different machine and see if it's even being detected. Kinda sounds like the drive just ate it. :(

---

### Post by alphaamanitin on 2010-09-29
Okay.  I have got it mounted on my normal machine, but it shows up as having ~270 gb free out of the 320 gb drive.  I only deleted my /lib that is it.  Shouldn't I be able to mount it and recover the files I did not delete?  

I am in the process of creating a Ubuntu USB pen drive to try to mount the drive with.  I am very confused about this.  I couldn't have deleted everythign could I?  

Will report back with more shortly.

AlphaA

---

### Post by alphaamanitin on 2010-09-29
Okay, it mounts as having no files or folders.  hmm I may have encrypted my home folder.  I really don't remember if I did or not.  I know the password if I did do so, but how would I go about getting access if I did?

AlphaA

EDIT:  I am now sure I did select the 'encrypt home' or whatever it is while installing Ubuntu.  I know the password though, so is there away around this.  I am guessing this also explains the chroot error.  However, I just read a bit of info about this type of thing and it says there should be some files there.  My drive shows up as completely empty, ls, ls -l and dir all show the drive as being empty.

AlphaA

---

### Post by alphaamanitin on 2010-10-01
Gave up and did a reinstall.  I think I just borked it too hard to restore.  I lost the files, but oh well.  Nothing serious.  I am making the thread as solved. 

AlphaA

Edit:  chroot did not work because I had mounted the drive I destroyed and most of the commands were lost as well.  There for when I tried to chroot that command was lost and nothing worked.  I believe this is the cause.  Lesson learned, never rm /lib  bad things happen.

---

