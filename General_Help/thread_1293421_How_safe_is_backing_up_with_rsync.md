---
title: "How safe is backing up with rsync"
date: 2009-10-17
forum: General Help
---

### Post by SoftwareExplorer on 2009-10-17
Hi,
I currently have /home on a separate partition that is rsync backed up fairly often. My main question is that I want to start backing up / with rsync, but is that safe? Will it restore properly? 
I was considering, if only some of the folders in / would backup properly is to move the ones that would onto the partition that /home is on and make symlinks to them.
So can I back up / on a running system with rysnc and have it restore fine? 
Can I back up with rsync a partition that has an ubuntu install on it that isn't currently running and have it restore properly?

Typically, I use rysc in archive mode in case you were worried about that.

EDIT:Maybe it would be clearer if I stated my goal.
Goal 1(Optimal way to have it):If the ubuntu partition accidentally gets hosed, I can rsync or copy all the files back and boot the last backup
---------or-------
less optimal
2 If the ubuntu partition gets accidentally messed up, I have to reinstall, but I can copy individual config files from the backup

---

### Post by SoftwareExplorer on 2009-10-30
Basically, if I were to make an empty ext3 or ext4 partition and copy the files in / on one system to that partition, would it boot with the proper grub entries?

---

### Post by alphaniner on 2009-10-30
You could have problems if you try coping system files from an active system.  

If you actually intend to backup and not clone, there are probably better tools, such as partimage or dump.

---

### Post by SoftwareExplorer on 2009-10-30
Thanks alphaniner. (I like your signature)
I could do it booted into another install or off a live cd. The main reason I want to know if it is possible to back up at the filesystem level is that my root partition is on ext4, and AFAIK partimage doesn't yet support it. I don't know about dump, but from a quick googling, ext4 support sounds like it is bleeding edge. (Though I don't know that for sure, I check when I'm not so tired). I could possibly use fsarchiver, (again, it runs at the filesystem level), but rysnc's delta transfer is nice and it is installed by default, which is easier when you are booting a live cd. Mostly, the easier it is to backup, the more often it happens.

---

### Post by alphaniner on 2009-10-30
I didn't think about the ext4 issue.

I'm just not sure about the feasibility of doing a full backup on a running system.  There's the /proc directory, I'm not sure how to handle that.  Plus you have to be sure your command doesn't backup any secondary mounted filesystems (such as the one you are backing up to).

But I'm sure there are tutorials out there that will be more useful than me.  Good luck.

---

### Post by SoftwareExplorer on 2009-10-31
> **alphaniner said:**
> I didn't think about the ext4 issue.

I'm just not sure about the feasibility of doing a full backup on a running system.  There's the /proc directory, I'm not sure how to handle that.  Plus you have to be sure your command doesn't backup any secondary mounted filesystems (such as the one you are backing up to).

But I'm sure there are tutorials out there that will be more useful than me.  Good luck.
Thanks alphaniner, for telling me what to watch out for.
I can prevent rsync from crossing filesystem boundaries with -x. And I'm rsyncing over ssh to a separate computer, because I don't really consider it a safe backup to have it on the same computer. (I've have had a computer power supply ruin all the drives that it powered before)

To anyone/everyone
I tried restoring to a different partition last night, and I change /etc/fstab and edited the old grub entry and it booted just fine, and as far as I could tell it was using just the partition I restored to. I also tried restorting a partition with karmic testing on it that had grub installed to the partition, but it wouldn't chainload, I think I would just have to set up the proper entries in menu.lst and it could boot the kernel instead of going from grub 1 to grub 2 and then karmic kernel.

So, it seems to work if you use -x and -a. -v will tell you what's happening, and -z will compress the data. To get it to use ssh, I use '-e ssh'

---

### Post by RandomJoe on 2009-10-31
What I have done in the past is to rsync the whole system but exclude certain directories (/dev, /sys, /proc, /mnt, whatever you know isn't really needed).  Then, when I did a restore, I did it in two steps - install the base OS to the drive, then rsync everything back on top of it.  That put all the customizations and any added software back on.

I haven't had to do that in quite a long time, but at the time it worked just fine.  I su to root to do that backup, to have full access to everything.  Never bothered to see if a 'sudo' would work properly.

---

### Post by SoftwareExplorer on 2009-10-31
I forgot to say I always use sudo. I don't want a backup that is missing system files because I didn't bother to make sure I had permission to read them. The only permission denied errors I get is for .gvfs in each user's home folder, but that's were stuff is mounted anyway, so it's fine with me if it doesn't work to back up all the windows shares you currently have mounted.

---

### Post by OldGrantonian on 2009-12-18
> **SoftwareExplorer said:**
> 
Goal 1(Optimal way to have it):If the ubuntu partition accidentally gets hosed, I can rsync or copy all the files back and boot the last backup
---------or-------
less optimal
2 If the ubuntu partition gets accidentally messed up, I have to reinstall, but I can copy individual config files from the backup

Hi Software Explorer,

Did you achieve the goal that you stated in your original post?
.

---

### Post by Ordes on 2009-12-18
I only sync my Data (/home, + additional drives) on my backup server using unison. Never had problems so far.

I was long looking for a way to backup the system, until i found remastersys. I love it. It creates an Live-ISO of your running system (including /home if u want; i never include as its too much data). After the iso is done, i put it on my usb. And i have a running Live version of my current Ubu with all my apps,etc..And the reinstall is just one click away.

[http://geekconnection.org/remastersys/ubuntu.html]("http://geekconnection.org/remastersys/ubuntu.html")

---

### Post by OldGrantonian on 2009-12-19
> **Ordes said:**
> 
I was long looking for a way to backup the system, until i found remastersys.

That looks very impressive :)

I didn't look at your post until after I tried fsarchiver (by one of the partimage developers). It's great :)

It creates an image partition, but only for the amount of data on the partition (1.1GB). It takes 3 minutes to restore my system partition. (My /home partition is separate. I use rsync for that because it's incremental.)

[http://www.fsarchiver.org/QuickStart](http://www.fsarchiver.org/QuickStart)
.

---

### Post by Quarkrad on 2009-12-19
Two questions please on fsarchiver

1.  Have you proved this working with an ext4 partition?
2.  I have a dual boot system, winxp on sda1 (1st partition on HD) and 9.10 on sda5 (2nd partition on HD).  If I used fsarchiver to backup 9.10/sda5 will it also restore grub2?  

I currently use clonezilla to backup and restore my Ubuntu system/partition but when I do this I'm left with a broken system because Grub2 is not restored.  Although I do not restore often I have to rebuild Grub2 manually to get back to a working PC.

---

### Post by OldGrantonian on 2009-12-19
> **Quarkrad said:**
> Have you proved this working with an ext4 partition?


I use Karmic with ext4 partitions. (partimage does not handle ext4.)

> **Quarkrad said:**
> 
I have a dual boot system, winxp on sda1 (1st partition on HD) and 9.10 on sda5 (2nd partition on HD). If I used fsarchiver to backup 9.10/sda5 will it also restore grub2?


I also have a dual-boot XP + Karmic :)

Everything seems to work fine.

I used two tests. 

Test 1: simple

1)  Use fsarchiver to clone the system partition to an external HDD. (I have a /home partition, but I use rsync for that, because it's incremental.)

2)  Make some known configuration changes to my setup. Add some stuff, remove some stuff. 

3)  Restore the fsarchiver clone. Verify that all my manual changes were restored to the pre-test configuration.

Test 2:  re-install

1)  Re-install Karmic from the ISO CD.

2)  Restore the fsarchiver clone.

3)  As before, verify that my pre-test configuration is restored.

BTW:  There was a fault during the reboot after restoring the clone. In each case, a partition could not be mounted.

I could see from the posts that this is common with 9.10 during updates. I'm no geek, but I simply edited fstab to correct a single entry, and the reboot continued OK.
.

---

### Post by Lukas666 on 2009-12-19
> **SoftwareExplorer said:**
> Thanks alphaniner. (I like your signature)
I could do it booted into another install or off a live cd. 

Please try clonezilla. I use it for full partition backups and I am very happy. It boots off a live CD.  Backing up my 1TB drive (8 partitions) about 300GB full takes about 2 hours.

---

### Post by Quarkrad on 2009-12-19
I agree Clonezilla is great but (on 9.10/ext4) it does not restore grub so although everything is restore back you have a broken pc.  You have to rebuild grub manually to fix.

---

### Post by Lukas666 on 2009-12-19
> **Quarkrad said:**
> I agree Clonezilla is great but (on 9.10/ext4) it does not restore grub so although everything is restore back you have a broken pc.  You have to rebuild grub manually to fix.

For me it does it too (I use "device to device" mode).

---

### Post by Lukas666 on 2009-12-19
> **Quarkrad said:**
> I agree Clonezilla is great but (on 9.10/ext4) it does not restore grub so although everything is restore back you have a broken pc.  You have to rebuild grub manually to fix.

For me it does it too (I use "device to device" mode).

---

### Post by SoftwareExplorer on 2009-12-20
I would like to say that I succeeded in goal #1. I backed up using rsync while the system was running (with -x option to prevent crossing filesystems) and then restored into a just formatted partition on a different computer. I made sure that grub had the right options so that I would be able to boot it, and restarted. I started it and the only two problems I had was that the (9.04 version) boot splash was to big (probably because of being on a different computer) and that a filesystem I had listed in fstab didn't exist because the restored system was on a different computer. If I was restoring on to the same computer I think it would have worked perfectly. 

So, rsync worked great for me. I didn't have to reinstall ubuntu before restoring like RandomJoe said. If something goes wrong (disk dies or something) then all I have to do to restore is fire up a live CD and make partitions, rsync everything back, set up grub (with like 3 easy steps).

---

### Post by OldGrantonian on 2009-12-21
> **SoftwareExplorer said:**
> I would like to say that I succeeded in goal #1.

You seem to have achieved what I wanted to do with rsync :)

I never succeeded, so that's why I'm trying fsarchiver.

I can rsync my /home partition OK. But the / partition gave only an incomplete (but working) restore. I still had to do some manual tweaking to my wireless and DVD.

I would be most grateful if you could show me your exclude file and your rsync script. 

My script is intended to produce a "mirror":

```

sudo rsync --dryrun -avvu --delete --exclude-from '/home/alan/Documents/Ubuntu/misc/rsync_excludeFile/rsync_excludeFile.txt'  /   /media/UbuntuBackup/rsync/slash/

```My exclude file was mainly copied from here:
[http://aplawrence.com/Bofcusm/2409.html](http://aplawrence.com/Bofcusm/2409.html)

```

### transient directories - contents
### tmp ###
+ tmp/
- **/tmp/**
+ /tmpfs/
- /tmpfs/**
### transient ###
+ /proc/
- /proc/**
+ /mnt/
- /mnt/**
+ /media/
- /media/**
### /home
- /home/
### cache ###
# mozilla
+ Cache/
- **/Cache/**
# ccache.samba.org
+ ccache/
- **/ccache/**
+ .ccache/
- **/.ccache/**
# others
+ cache/
- **/cache/**
+ xover-cache/
- **/xover-cache/**
### obj ###
# kernel build
- usr/src/**.o
# special library .o (may be RH specific?)
+ usr/*/lib/**.o
+ usr/lib/**.o
# all others
- *.o
### backup ###
- *~

```.

---

### Post by SoftwareExplorer on 2009-12-21
Well, here's what I run to back up my desktop computer. /media/Data-500 has /home and lots of other user files on it, and nothing is mounted under it.
```
sudo rsync -e ssh -avz /media/Data-500 192.168.0.7:/media/Backup/bjorn-desktop/rsync
sudo rsync -e ssh -avxz --delete-after / 192.168.0.7:/media/Backup/bjorn-desktop/rsync/karmicroot

```
As you can see I don't currently use an exclude. If I run 'mount' (with no parameters) it will list all the mounted filesytems (which would be excluded because of -x, except for /media/Data-500). On my computer I get ```
bjorn@bjorn-desktop$ mount
/dev/sda2 on / type ext4 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
none on /var/lib/ureadahead/debugfs type debugfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sdb2 on /media/Data-500 type ext3 (rw,nosuid,nodev)
gvfs-fuse-daemon on /media/Data-500/home/bjorn/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=bjorn)

```
(if you're wondering about /home, it's a symlink to /media/Data-500/home)

Also, do you mind elaborating on what you had to fix with DVDs and wireless, and I'll try to see if I have the same problems?

---

### Post by OldGrantonian on 2009-12-22
> **SoftwareExplorer said:**
> 
Well, here's what I run to back up my desktop computer......


Your command worked great. Thanks for that :)

I think my whole rsync setup that I posted earlier was probably far too complicated. But, as I said, it was copied from someone else on the internet, and I wanted to copy someone who had actually succeeded.

I tested the backup by using rm -rf * on the / partition :)

Now I feel like a geek (or at least a second-deputy chief-assistant under-geek) :)

> **SoftwareExplorer said:**
> 
Also, do you mind elaborating on what you had to fix with DVDs and wireless, and I'll try to see if I have the same problems?


Both DVD and wireless were fine. As I said earlier, I think my command (plus exclude file) was too elaborate. Maybe some options were clashing with other options.

Thanks again :)

------------------------------------------

For the benefit of anyone else, here's my command using SystemRescueCD:

rsync  -avx  --delete-delay  /mnt/backup_laptop/  /mnt/backup_hdd/rsync/slash/

Note1:  that I don't use -z (compression) because I have a massive HDD, and I like to see individual files.

Note2:  according to the man pages, --delete-delay is more efficient than --delete-after

Note3: I don't need -e (SSH). It's a local HDD.

Note4: I have a separate /home partition
.

---

### Post by SoftwareExplorer on 2009-12-22
> **OldGrantonian said:**
> Your command worked great. Thanks for that :)
....
Thanks again :)

You're welcome. :)
> **OldGrantonian said:**
> 
Note1:  that I don't use -z (compression) because I have a massive HDD, and I like to see individual files.

Note2:  according to the man pages, --delete-delay is more efficient than --delete-after

From what I understand, -z just compresses the data that is sent over the network. On my backup computer I can see all the individual files. So it doesn't even apply if you are doing only local backups.
As far as delete-delay, I'll try it, my backup computer does slow down quite a bit when a backup is deleting old files.

---

