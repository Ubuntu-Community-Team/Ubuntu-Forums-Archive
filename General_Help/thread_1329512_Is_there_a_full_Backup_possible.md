---
title: "Is there a full Backup possible?"
date: 2009-11-17
forum: General Help
---

### Post by milenixloerdi on 2009-11-17
Hi,

Is there a way to "save" all already installed programs/hardware configurations/etc in a form of a "backup" which can be used in case of a failure and complete re-install of Ubuntu? I know about the copy/paste of the /home folder, but that does not include configurations or programs.

Im not being "negative", but since I am new to Ubuntu I can do mistakes - and if I have to re-install completely, it will be lovely if I can restore all my settings and programs through such backup, if possible.

Thanks

---

### Post by tea for one on 2009-11-17
To back up your OS including added software, you may wish to explore Remastersys and I found this website very useful.

[http://www.dedoimedo.com/computers/remastersys.html](http://www.dedoimedo.com/computers/remastersys.html)

To back up your data including hidden files in your home directory, I would suggest you explore Grsync available via Synaptic

Kind regards

---

### Post by ikislav on 2009-11-17
I'm new to Ubuntu myself and I am looking forward to see what experienced users are going to say on this topic.

---

### Post by phillw on 2009-11-17
There is an excellent talk about backups and restoring over this way --> [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

I use the script myself, although thankfully, never had to restore

Regards,

Phill.

---

### Post by booksnmore4you on 2009-11-17
Remastersys is wonderful. It is simple and almost "dummy proof".

Just keep in mind that it will not make an ISO larger than will fit on a single layer DVD, a bit over 4 gigs.

In my case, I had to separately back up my personal non-hidden files in my home directory, which alone were well over 4 gigs.  Then I deleted my personal files from home and then proceed with my Remastersys backup.

A huge advantage of  Remastersys is that I am now fearlessly bold to experiment with my system. If worse comes to worst, I just reinstall my "perfect" system.

---

### Post by Giblet5 on 2009-11-17
You'll need an ext3 filesystem that's as big as your system.

I will assume that you mounted this second drive at /mnt

```
sudo tar -cPjf /mnt/backup.tar.bzip2 /
```


That will back up *everything*.


To restore, perform a normal reinstall, mount that extra backup drive on /mnt and enter:

```
cd /
tar xjf /mnt/backup.tar.bzip2
sudo grub-install `grep hd0 /boot/grub/device.map | tail -1 | awk '{ print $2 }'`
sync;sync
sudo reboot --force
```

That will put you right back where you were when you ran the backup. Even the grub menu will be the same.

---

### Post by louieb on 2009-11-17
I'm  a fan of** partimage **Its got a old style text based n-cursors interface. 

[Howto: Backup with Partimage - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=287522") 

I use it to backup before making major changes (like upgrading from Jaunty to Karmic).  And from experience It will restore your system to state it was in when you took the backup.

:rolleyes: Unfortunately looks like I'm going to have to find something else. partimage does not support ext4.  Going to take a look at [FSArchiver]("http://www.fsarchiver.org/").

---

