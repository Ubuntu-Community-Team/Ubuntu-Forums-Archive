---
title: "Windows X and System TIme"
date: 2010-05-24
forum: General Help
---

### Post by towka on 2010-05-24
Hello everybody!
I have the  following problem.
I have studied the C/C++ library functions work with the system  time (POSIX).
Changed the date to come for 2 years.
The following sample code in C/C++:
```
void  set_time (T * t, TP * tp)
(
tp-> tm_hour = 21;
tp-> tm_min =  42;
tp-> tm_sec = 29;
tp-> tm_mday = 20;
tp-> tm_mon =  0;
tp-> tm_year = 2012 - 1900;
    tp-> tm_isdst =  -1;
    t-> tv_sec = mktime (tp);
    clock_settime  (CLOCK_REALTIME, t);
)

```

After the  restoration date for today's date and restart PC the X does not start -  only a black screen. Logs in X.org issue no errors.
I read on the  Internet that the system locks that after the transition time in the  future. And that system is blocked - I do not  know.
How do I fix?
Thank you.

---

### Post by happyhamster on 2010-05-24
Try setting the time to the old value in the computer's BIOS. You'll have to press some key during the very early stages of the boot process to bring up the BIOS screen. (Often it's the delete key, but it might be any other. The exact key is usually shown at the bottom of the very first bootscreen.)

Good luck.

---

### Post by towka on 2010-05-24
> **happyhamster said:**
> Try setting the time to the old value in the computer's BIOS.

Thank you for your reply. 
I &#1089;hanged the time in the  BIOS. Now, instead of running  the X system requests the password  root (as in recovery mode). 
After entering a  password, I get this message: Mount error file system. 
I looked at the output of  mount. It seems the correct root  partition is mounted, and in the mode of RW. I tried to start X  (startx or gdm). And I will receive a message including "Can not write a  certain file. Filesystems in ro mode"

Any ideas?:confused:

---

### Post by happyhamster on 2010-05-24
Do you have a live-cd? In that case try booting from the cd into a live-session so you can safely run a disk-check. This is also a good opportunity to backup your data BTW. If you want to backup your files, you'll have to mount the hard-drive first. Start nautilus (Places-->Home Folder), and the partition(s) should be visible at the left pane (..GB Filesystem): right-click to mount. You can now backup your data to an usb-stick or such.

- Next, to run the disk-check: the harddrive must NOT be mounted in this case. Again, go to nautilus and right-click the partitions to unmount them. This is important, because running fsck on a mounted filesystem could do damage to it.

- Next, find the name of the partitions on your drive:

sudo fdisk -l

- It should output all partitions found, usually /dev/sda1, /dev/sda2, etc. Make a note of them. Next, to double-check, see if they are truly unmounted:

mount

- The hard drive partitions should NOT be visible in that list. Next, run fsck on them:

sudo fsck /dev/sda1

- Repeat for all your partitions. There may be some error output (for swap or extended partitions). Reboot.


Good luck.

---

### Post by towka on 2010-05-25
> **happyhamster said:**
> 
Do you have a live-cd? 
......
Good luck.

As I followed your  advice. On the hard drives were  errors and fsck to check them. 
After restarting, I got  into a situation that existed before the change of time in the BIOS. 
Then I went through all  the logs in / logs - nothing suspicious found. 
It's just a horror =) 

In short, I think to make  a copy of important files (home directory and other settings program)  to another disk. 

And try out the new  ubuntu 10.4. This is certainly not  going to do, but later. 




If anyone has another  idea how to restore an existing system, I ask you to reply here. I still try to restore  it. 
Thank you.

---

