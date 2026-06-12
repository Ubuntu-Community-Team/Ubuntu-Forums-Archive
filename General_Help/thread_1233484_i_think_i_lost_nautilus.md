---
title: "i think i lost nautilus"
date: 2009-08-06
forum: General Help
---

### Post by nugurl on 2009-08-06
I apoligize if this is a simple problem, but its pretty far beond me.
 
I recently installed ubuntu 9.04 (my very first linux install, so please bear with me.)  I wasnt able to open any folders, the files were there i could access them through other programs, but if i tried to open my music folder it would just say opening music and then disaper.  So after some searching i figured out that nautilus was the thing that was supposed to be doing that.  So i ran the disk checker on my instalation disk, and it came back fine.  I reinstalled ubuntu, it still didnt work, so i found a copy of nautilus, put it on a thumb drive, and reinstalled ubuntu with the thumb drive in the computer.  Once that was done, i copied nautilus from the thumb drive to the desktop and rebooted without the thumb drive attached.  That worked for a while.  But after a few days it seemed to disaper again.  I still have it on the thumb drive, but i dont know how to access it without opening it in, well, nautilus file manager.  And i dont want to be reinstalling ubuntu every few days.
 
Any help?  preferably in small, easy to understand words?:oops:

---

### Post by michy99 on 2009-08-06
If you enter the word nautilus in a terminal, do you get any error messages?

---

### Post by nugurl on 2009-08-06
im not sure, how do i do that?
 
like i said, reeeeeely new.:oops:

---

### Post by michy99 on 2009-08-06
Applications->Accessories->Terminal. Enter this command:```
nautilus
```

---

### Post by nugurl on 2009-08-06
GLib-ERROR **: /build/buildd//glib2.0-2.20.1/glib/gmem.c:156:  failed to allocate 1073741824 bytes
aborting...
Aborted
[EMAIL="user@user-desktop:~$"]user@user-desktop:~$[/EMAIL]

---

### Post by michy99 on 2009-08-06
Enter this command in the terminal and tell me what it says:```
df -h
```

---

### Post by nugurl on 2009-08-06
Filesystem      Size   Used  Avail Use%  Mounted on
/dev/sdal       113G  2.3G  105G    3%  /
tmpfs            119M        0  119M   0%  /lib/init/rw
varrun           119M    92K  119M   1%  /var/run
varlock          119M       0   119M   0% /var/lock
udev             119M    148K 119M   1% /dev
tmpfs            119M    192K 119M   1% /dev/shm
lrm               119M    2.4M  117M  2%  /lib/modules/2.6.28-11-generic/volatile
/dev/sub       7.9G     85M   7.8G   2% /media/user

---

### Post by michy99 on 2009-08-06
It's got to be more than that. You should get something that looks like this:```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              12G  7.7G  3.7G  68% /
tmpfs                 122M     0  122M   0% /lib/init/rw
varrun                122M  224K  122M   1% /var/run
varlock               122M     0  122M   0% /var/lock
udev                  122M  164K  122M   1% /dev
tmpfs                 122M   76K  122M   1% /dev/shm
lrm                   122M  2.2M  120M   2% /lib/modules/2.6.28-14-generic/volatile
/dev/sda4              12G  6.0G  4.6G  57% /home
/dev/sda1              14G  9.9G  3.5G  74% /media/MWIN
/dev/sdb1              13G   11G  1.9G  85% /media/storage
/dev/sr1              4.0G  4.0G     0 100% /media/v104
/dev/mapper/truecrypt1
                      4.0G  3.5G  375M  91% /media/truecrypt1

```Use copy and paste to post it here.

---

### Post by nugurl on 2009-08-06
sorry, i posted by accedent.  i cant copy paste, because im on a different computer.

---

### Post by michy99 on 2009-08-06
I am mainly interested in the first line after the line that says Filesystem. The line that ends with /

---

### Post by nugurl on 2009-08-06
/dev/sdal 113G   2.3G   105G   3%   /
 
is it bad?

---

### Post by michy99 on 2009-08-06
Nope. You have plenty of space on your partition, so that isn't the problem. If you enter this command```
sudo fdisk -l
```Do you see a line that contains the word swap? (That's an l as in lion, not the number 1)

Also, how much memory does your computer have?

---

### Post by nugurl on 2009-08-06
yep, says
 
/dev/sda5     14860     14946   698796    82  Linux swap / Solaris
 
Thers also a massage saying  "This doesnt look like a partition table  Probably you selected the wrong device"
 
then theres a table that says none of my four partitions end in a cylinder boundary.
 
Not sure if that last bit was relevent, but it looked odd, so i tought id mention it.
 
I also have no idea how much memory my system has, but since its been sitting in my basement for at least 6 years, im gonna guess its on the low end.

---

### Post by michy99 on 2009-08-06
System->Administration->System Monitor. That will tell you how much memory you have.

---

### Post by nugurl on 2009-08-06
237.1 MB  and a 682.4MB Swap

---

### Post by michy99 on 2009-08-06
Enter this in a terminal to re-install nautilus:```
sudo apt-get install --reinstall nautilus
```

---

### Post by nugurl on 2009-08-06
its telling me 'reinstallation of nautilus is not possible, since it cannot be downloaded'
 
I still have it on my usb stick and (mabey) on the install disk, is it possible to specify one of those as a source?

---

### Post by Seq on 2009-08-06
> **nugurl said:**
> GLib-ERROR **: /build/buildd//glib2.0-2.20.1/glib/gmem.c:156:  failed to allocate 1073741824 bytes
aborting...
Aborted
[EMAIL="user@user-desktop:~$"]user@user-desktop:~$[/EMAIL]

> **nugurl said:**
> 237.1 MB  and a 682.4MB Swap

I'd say you're low on memory, judging by the error. 256MB is the low end of what I'd run Ubuntu on (xubuntu might manage better). What does the output of `free -m` say? Mine looks like this:
```
[chris@macbook:~]$ free -m
             total       used       free     shared    buffers     cached
Mem:          3924       2078       1845          0        228        802
-/+ buffers/cache:       1047       2876
Swap:         5119          0       5119
```

What this says is that my machine has in total 3924MB ram and I have 1845MB free. Note that even if Free was 0, I still have 802MB as cache that could be re-allocated to programs. I'd be curious to see if you have a very low number as 'free' and 'cached', which would indicate you're running out of memory.

More swap space is somewhat important here as it can compensate for low memory, but will be rather slow.

---

