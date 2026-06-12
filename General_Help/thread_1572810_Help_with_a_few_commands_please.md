---
title: "Help with a few commands please"
date: 2010-09-11
forum: General Help
---

### Post by Kir_B on 2010-09-11
Hey folks.

I'm trying to follow a few commands that have been recommended to to get my system to boot again and could use a little guidance please. 

The following are the commands:
```
sudo mkdir /mnt/hdd
sudo mount /dev/sda6 /mnt/hdd 
```Then modify the **first command** I gave you to read:
     ```
cd /mnt/hdd/etc/init.d 
```All other commands should work:
```
sudo mv plymouth plymouth.bak
sudo mv plymouth-log plymouth-log.bak
sudo mv plymouth-splash plymouth-splash.bak
sudo mv plymouth-stop plymouth-stop.bak
```At the end, you should also run the following commands:
```
sudo update-rc.d plymouth remove
sudo update-rc.d plymouth-log remove
sudo update-rc.d plymouth-splash remove
sudo update-rc.d plymouth-stop remove 
```And here is the terminal readout from the first few  commands: 
```
ubuntu@ubuntu:~$ sudo mount /dev/sda6 /mnt/hdd
mount: /dev/sda6 already mounted or /mnt/hdd busy
mount: according to mtab, /dev/sda6 is already mounted on /mnt/hdd
ubuntu@ubuntu:~$ cd /mnt/hdd/etc/init.d
ubuntu@ubuntu:/mnt/hdd/etc/init.d$ sudo mv plymouth plymouth.bak
ubuntu@ubuntu:/mnt/hdd/etc/init.d$ sudo mv plymouth-log plymouth-log.bak
ubuntu@ubuntu:/mnt/hdd/etc/init.d$ sudo mv plymouth-splash plymouth-splash.bak
ubuntu@ubuntu:/mnt/hdd/etc/init.d$ sudo mv plymouth-stop plymouth-stop.bak
ubuntu@ubuntu:/mnt/hdd/etc/init.d$ sudo update-rc.d plymouth remove
update-rc.d: /etc/init.d/plymouth exists during rc.d purge (use -f to force)
ubuntu@ubuntu:/mnt/hdd/etc/init.d$ 
```Am I right that at this point I should issue the " -f " command or should I issue the -f at the end of the last command?

Just thought it might be wise to inquire before going ahead.

Thanks a tonne. KIrby

---

### Post by Kir_B on 2010-09-11
I just edited the first post to include everything that I've been told to do, as I misunderstood the instructions from [here]("http://ubuntuforums.org/showpost.php?p=9830900&postcount=10") and [here]("http://ubuntuforums.org/showthread.php?p=9834488#post9834488").

Hopefully this makes things a little more clear.

Thanks Kirby

---

### Post by AlphaLexman on 2010-09-11
Are you having trouble mounting /dev/hda6/ or are you having trouble moving/copying files?

---

### Post by Kir_B on 2010-09-11
Thanks for the reply.

I'm unsure of the process to force that is mentioned in the terminal readout. I'm operating off of a livecd and it's acting up, or I would have responded much, much sooner.

Thanks again. Kirby

---

### Post by AlphaLexman on 2010-09-11
It seems you have some files on /dev/sda6/
From a terminal post the output of:
```
mount
```
so we can see if and how it is mounted.

---

### Post by Kir_B on 2010-09-11
> **AlphaLexman said:**
> It seems you have some files on /dev/sda6/
From a terminal post the output of:
```
mount
```so we can see if and how it is mounted.

Thanks and here it is:

```
ubuntu@ubuntu:~$ mount
aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdb on /media/New Volume type vfat (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sda6 on /mnt/hdd type ext3 (rw)
ubuntu@ubuntu:~$ 
```

---

### Post by AlphaLexman on 2010-09-11
The LAST line:
> /dev/sda6 on /mnt/hdd type ext3 (rw)
says it's mounted as read/write, are you still having trouble moving or copying files?

---

### Post by Kir_B on 2010-09-11
No problem so far, see below:

```
ubuntu@ubuntu:~$ sudo mount /dev/sda6 /mnt/hdd
mount: /dev/sda6 already mounted or /mnt/hdd busy
mount: according to mtab, /dev/sda6 is already mounted on /mnt/hdd
ubuntu@ubuntu:~$ cd /mnt/hdd/etc/init.d
ubuntu@ubuntu:/mnt/hdd/etc/init.d$ sudo mv plymouth plymouth.bak
ubuntu@ubuntu:/mnt/hdd/etc/init.d$ sudo mv plymouth-log plymouth-log.bak
ubuntu@ubuntu:/mnt/hdd/etc/init.d$ sudo mv plymouth-splash plymouth-splash.bak
ubuntu@ubuntu:/mnt/hdd/etc/init.d$ sudo mv plymouth-stop plymouth-stop.bak
ubuntu@ubuntu:/mnt/hdd/etc/init.d$ sudo update-rc.d plymouth remove
update-rc.d: /etc/init.d/plymouth exists during rc.d purge[COLOR=Red] (use -f to force)[/COLOR]
ubuntu@ubuntu:/mnt/hdd/etc/init.d$ 
```It's the force portion. Do I just do -f at this point, or do I issue the following command:

```
sudo update-rc.d plymouth remove -f
```Thanks again. Kirby

---

### Post by AlphaLexman on 2010-09-11
> It's the force portion.
If your backups were successful, it should be OK to use the 'force' option.

---

### Post by Kir_B on 2010-09-11
So, the command that I posted above is correct?

I really don't want to make a mess, that's all.

Thanks a tonne. Kirby

---

