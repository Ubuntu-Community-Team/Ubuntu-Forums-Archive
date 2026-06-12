---
title: "Strange disk usage computation after upgrade to ubuntu 10.04"
date: 2010-05-04
forum: General Help
---

### Post by texis on 2010-05-04
Hi all,

I upgraded from 9.10 to 10.04 without any visible issues. But after a few days system started to behave strange - first it shows the message that gnome-power-manager is not correctly installed on login screen. The it wasn't able to log in even - so I found that the problem might be that it shows not enough space on the root partition.

This is really strange for me - I do not have any special data there.

See what I have after **df** command:
/dev/sda2              9614148   8618864    506908  95% /
none                   1024128       360   1023768   1% /dev
none                   1028632       184   1028448   1% /dev/shm
none                   1028632       124   1028508   1% /var/run
none                   1028632         0   1028632   0% /var/lock
none                   1028632         0   1028632   0% /lib/init/rw
none                   9614148   8618864    506908  95% /var/lib/ureadahead/debugfs
/dev/sda3              9614148   5847464   3278308  65% /home
/dev/sdb1            244196000  25490528 218705472  11% /media/Data
/dev/sdc1            488384000 266319412 222064588  55% /media/Filmy
/dev/sda4             30724312  25365696   5358616  83% /media/Zalohy

There is different partition for /home, and other stuff like movies etc. is on different disk.

But if I played with **du** I found that I have /usr/share about 2,8GB and other folders together are less than 1,5GB

**BUT** - I was suggested to try:
*find / -xdev  -type f -print0 | xargs -0 du | sort -g | gawk '{ sum += $0 }; END { print sum }'*

to count sizes manually and I've got **3169640** which makes sense.

Any idea what's wrong with **df**??

Thanks

Texis

---

### Post by dcstar on 2010-05-04
> **texis said:**
> 
.......
Any idea what's wrong with **df**??

Probably nothing:
```
gksudo baobab
```

---

### Post by texis on 2010-05-04
> **dcstar said:**
> Probably nothing:
```
gksudo baobab
```

It returns the same like using 

# du -sc * | sort -g
0	cdrom
0	initrd.img
0	lib64
0	proc
0	sys
0	vmlinuz
4	mnt
4	nonexistent
4	opt
4	selinux
4	srv
16	lost+found
64	tmp
544	dev
7324	sbin
7684	bin
9108	root
12400	lib32
17180	etc
19468	boot
160972	lib
330700	var
2717576	usr
5694888	home
316727716	media
325705660	total

Where home and media are different partitions than where / is mounted on.

---

### Post by john newbuntu on 2010-05-04
du -scx should exclude the mounts and give you the total.  
There is a discrepancy of 5+ gigs between du and df that is close to the size of your /home usage.  When you created /home on a separate partition, did you copy or move /home?  
If you are sure you copied, could you try to unmount /home and recheck your filesystem.

---

### Post by texis on 2010-05-04
> **john newbuntu said:**
> du -scx should exclude the mounts and give you the total.  
There is a discrepancy of 5+ gigs between du and df that is close to the size of your /home usage.  When you created /home on a separate partition, did you copy or move /home?  
If you are sure you copied, could you try to unmount /home and recheck your filesystem.

Good idea but no success. After unmounting /home there is nothing in "ls -a /home" and **df** still shows the same. Home itself has app. 5.8GB used.

---

### Post by dabl on 2010-05-04
Here's some information on disk utilization behavior:

[http://ubuntuforums.org/showthread.php?t=215177](http://ubuntuforums.org/showthread.php?t=215177)

---

### Post by texis on 2010-05-04
> **dabl said:**
> 95% for the "/" filesystem is pushing it.  Remember ext3/4 filesystems attempt to reserve approximately 5% free space, by default -- in your case this would leave zero available space.  I suspect your issues will clear up if you either find some things to delete, or enlarge the root partition.

[http://ubuntuforums.org/showthread.php?t=215177](http://ubuntuforums.org/showthread.php?t=215177)

Yea, that's what I did yesterday - but - real usage of the root partition (See above) is just about 3,2GB of 10GB

---

### Post by dabl on 2010-05-04
Yeah -- sorry, I edited -- I though it said "du" was 95%.

Is it ext4?

---

### Post by texis on 2010-05-04
> **dabl said:**
> Yeah -- sorry, I edited -- I though it said "du" was 95%.

Is it ext4?

Yes - ext4,

this happened just after upgrade to Ubuntu 10.04 - before I haven't noticed any issues with the free space. I also noticed some mess with mount points after upgrade - it created /media/Data_ with incorrect device together with original /media/Data  - no idea what happened - so I corrected whole /etc/fstab.

I also found similar bug related to use UUIDs within fstab so I've tried to use older /device /mountpoint fstab but the same result.

Also apt-get autoclean or autoremove or even fsck on / didn't changed anything.

:(

---

### Post by john newbuntu on 2010-05-04
I suppose you checked by unmounting /media/Data as well just like you did with /home?  Also check file sizes in /var/log (ls -lSrR) since du ignores open files.

---

### Post by texis on 2010-05-04
> **john newbuntu said:**
> I suppose you checked by unmounting /media/Data as well just like you did with /home?  Also check file sizes in /var/log (ls -lSrR) since du ignores open files.

You've got it - thanks - it was in /media - I've played with backup using rsync command and it created u new folder under /media instead of using /media/backups mounted disk.

---

