---
title: "/ Directory Gets Full, Then Can't Log into Ubu"
date: 2009-10-02
forum: General Help
---

### Post by ashikar on 2009-10-02
Hello,

I usually don't like to post help topics, but I read several other posts and either they don't apply to me or I simply don't understand their context :/

Moving on..
I am using Jaunty 64 bit and have encrypted my HDD except the boot using LVM ([http://kuparinen.org/martti/comp/ubuntu/en/cryptolvm.html](http://kuparinen.org/martti/comp/ubuntu/en/cryptolvm.html)).

Anyways, I left my computer on overnight and in the morning I noticed my / directory full %100. I couldn't mount or find usb drives etc. I deleted my /tmp and restarted only to find the following error after logon:

```
GDM could not write to your authorization file. This could 
mean that you are out of disk space or that your home 
directory could not be opened for writing. In any case, it 
is not possible to log in. Please contact your system administrator.
```After a few unsuccessful hours, I did a clean install and spent nearly a day seting up all my stuff.


Now its happening again, what do I do? I've tried cleaning the /tmp, unnecessary files etc.. I also have a suspicion that transmission, the bt client, might be to blame, but I set my firewall up pretty well etc... I'm scared and confused. :confused: Please help.

output: df -h 
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/lvm-root  9.2G  8.3G  476M  95% /
tmpfs                 1.9G     0  1.9G   0% /lib/init/rw
varrun                1.9G  104K  1.9G   1% /var/run
varlock               1.9G     0  1.9G   0% /var/lock
udev                  1.9G  176K  1.9G   1% /dev
tmpfs                 1.9G  160K  1.9G   1% /dev/shm
lrm                   1.9G  2.5M  1.9G   1% /lib/modules/2.6.28-15-generic/volatile
/dev/sda1             183M   35M  139M  20% /boot
/dev/mapper/lvm-home   20G  5.6G   14G  30% /home
/home/x/.Private       20G  5.6G   14G  30% /home/x
/dev/sdb1             1.9G  1.1G  754M  60% /media/disk
x@x:/$ sudo du -hx --max-depth=1 /

```output: sudo du -hx --max-depth=1 /
```
7.2M    /bin
16K    /lost+found
8.9M    /sbin
4.0K    /selinux
251M    /var
4.0K    /opt
0    /sys
4.0K    /home
44K    /media
0    /proc
4.0K    /mnt
14M    /etc
1.0K    /boot
32K    /tmp
4.0K    /srv
0    /dev
250M    /lib
2.6G    /usr
264K    /root
3.2G    /

```Thanks in advance!

PS:
Oh! Also, when I deleted my /tmp folder (about 4.3 GB at the time) and then emptied the trash this did not reflect in the df -h results.

---

### Post by ashikar on 2009-10-02
I updated the title. I should have named it this before.

---

### Post by drs305 on 2009-10-02
> **ashikar said:**
> PS:
Oh! Also, when I deleted my /tmp folder (about 4.3 GB at the time) and then emptied the trash this did not reflect in the df -h results.

How did you delete the trash? If this was trash owned by 'root' and you deleted it with Nautilus you must use SHIFT-DEL to permanently delete the trash from the Trash bin. If you just press the DEL key, the files will be moved to Trash, where they continue to take up space. This is okay, and is a good 'safety' feature, but to regain the space you must empty Root's trash. Do this by deleting the root Trash bin folder. Use SHIFT-DEL - using just DEL will just recycle the files back into the Trash bin.

To delete root's trash, open Nautilus with this command, then use SHIFT-DEL to remove the **Trash** folder. Trash's subfolders, *info* and *files* will also be deleted. These files will be restored the next time root deletes anything.
```

gksu nautilus /root/.local/share

```

Added: I wrote a guide about finding the causes of full partitions and how to restore free disk space:
[Recover Lost Disk Space]("http://ubuntuforums.org/showthread.php?t=1122670")

---

### Post by ashikar on 2009-10-02
Thanks that makes sense, but I can't find .local (yes know ctrl+h) but its just not there. Also when I do that I get this error:

[http://i34.tinypic.com/332qqnc.jpg](http://i34.tinypic.com/332qqnc.jpg)

it also spews out a bunch on the bash

---

### Post by ashikar on 2009-10-02
Another thing I have noticed is that my administrative pass seems to have been changed... If I execute programs from sudo in bash, it accepts my pass. If I run say firestarter or wireshark from the menu, it asks me for my pass, and then says its incorrect.

Also, firestarter and wireshark were exited somehow overnight, and firestarter just disabled it self randomly... or maybe not so randomly. I'll keep investigating.

---

### Post by ashikar on 2009-10-02
My system started to act strange so I took the risk to reboot my system and it loaded and the 4.3 GB  disappeared :) I still don't have .local in /root so I will have some research to do about my disk structures.

I also noticed that many of my firewall security features were somehow silently disabled. An excuse to harden my system :)

Thanks again drs305

---

