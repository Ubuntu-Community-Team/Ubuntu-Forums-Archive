---
title: "Hard drive fills without data"
date: 2010-09-27
forum: General Help
---

### Post by Dan409 on 2010-09-27
I have the strangest issue where my HDD reports full, but I can only account for about a tenth of the data. 
Specs: 
Ubuntu 10.4 
laptop Toshiba Tecra A11
HDD 250GB
4Gb RAM
/home 20.3GB
/usr 2.4GB
/var 742MB
/lib 132.9MB
/opt 71.3 MB
/boot 15.4MB
/etc 14.2MB
sbin 7.4MB
bin 6.4MB

The rest are below a MB. This system is not a dual boot so 241Gb is ext4 and 8.9Gb is Extended and 8.9GB is Swap. This system has been loaded for about a month, when I initially loaded it there was 230GB free. 
Thanks

---

### Post by mikewhatever on 2010-09-27
Can you post the output of the following command:
```
sudo du -s /* | sort -nr
```

---

### Post by Dan409 on 2010-09-27
> **mikewhatever said:**
> Can you post the output of the following command:
```
sudo du -s /* | sort -nr
```

Here is the output from that command. I see /usr using a massive amount, does that look like it could be the culprit? I will look at it's contents. 

du: cannot access `/home/deh/.gvfs': Permission denied
du: cannot access `/proc/7266/task/7266/fd/4': No such file or directory
du: cannot access `/proc/7266/task/7266/fdinfo/4': No such file or directory
du: cannot access `/proc/7266/fd/4': No such file or directory
du: cannot access `/proc/7266/fdinfo/4': No such file or directory
221922533	/media
21313444	/home
2511296	/usr
742932	/var
136048	/lib
72964	/opt
15776	/boot
14944	/etc
7608	/sbin
6568	/bin
640	/root
592	/dev
200	/srv
68	/tmp
16	/lost+found
4	/selinux
4	/mnt
4	/cdrom
0	/vmlinuz
0	/sys
0	/proc
0	/initrd.img

---

### Post by mikewhatever on 2010-09-27
No, /usr is about 2.5GB as you reported initially, everything else looks normal too. How about the output of **df -h** ?

---

### Post by Dan409 on 2010-09-27
> **mikewhatever said:**
> No, /usr is about 2.5GB as you reported initially, everything else looks normal too. How about the output of **df -h** ?

Here is that output. I see that /dev/sda1 which is my HDD says that 205GB is used but not sure where. 


Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             222G  205G  5.0G  98% /
none                  1.5G  480K  1.5G   1% /dev
none                  1.5G  252K  1.5G   1% /dev/shm
none                  1.5G  360K  1.5G   1% /var/run
none                  1.5G     0  1.5G   0% /var/lock
none                  1.5G     0  1.5G   0% /lib/init/rw
/dev/sdb1              75G   18G   58G  24% /media/EDGE_DISKGO_
/dev/sdc1             233G   14G  220G   6% /media/FreeAgent Drive

---

### Post by mikewhatever on 2010-09-27
Hm ..., very odd indeed.:confused:

---

### Post by andrewthomas on 2010-09-27
take a screenshot of the output of applications > accessories > disk usage analyzer - scan home

---

### Post by Dan409 on 2010-09-27
> **mikewhatever said:**
> Hm ..., very odd indeed.:confused:

Yes, very odd, I am not sure if it would be better to do a backup, which is only 12GB, then do a complete re-install of the OS followed by a backup-recovery.

---

### Post by Dan409 on 2010-09-27
> **andrewthomas said:**
> take a screenshot of the output of applications > accessories > disk usage analyzer - scan home

I could but it only shows that 20.3GB is used by home.

---

### Post by The Cog on 2010-09-27
There is 200G in / according to df, but it doesn't seem to be showing up in du. So I wonder if it's in /media, and hidden because an external media is mounted over the top of it. Try removing the freeagent and edgedisk external drives, and try du again.

---

### Post by mikewhatever on 2010-09-27
> **Dan409 said:**
> Yes, very odd, I am not sure if it would be better to do a backup, which is only 12GB, then do a complete re-install of the OS followed by a backup-recovery.

Backing up is always a good idea, reinstall or not.

---

