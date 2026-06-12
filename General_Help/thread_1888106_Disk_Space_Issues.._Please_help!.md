---
title: "Disk Space Issues.. Please help!"
date: 2011-11-28
forum: General Help
---

### Post by illuminate1 on 2011-11-28
First, I apologize for my complete noob-ness. We all start somewhere right? So here is my issue, / is at 100%:

```
root@server01:/# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/cciss/c0d0p1     129G  129G     0 100% /
none                  1.9G  232K  1.9G   1% /dev
none                  1.9G     0  1.9G   0% /dev/shm
none                  1.9G  104K  1.9G   1% /var/run
none                  1.9G     0  1.9G   0% /var/lock
none                  1.9G     0  1.9G   0% /lib/init/rw
/dev/cciss/c0d1p1     270G  177G   79G  70% /backups
/dev/sda1             8.1T  370G  7.3T   5% /backups2
``````
root@server01:/# du -sh *
177G    backups
369G    backups2
6.5M    bin
16M     boot
4.0K    cdrom
4.0K    data
232K    dev
14M     etc
2.2M    home
0       initrd.img
131M    lib
16K     lost+found
8.0K    media
8.0K    mnt
4.0K    opt
du: cannot access `proc/2626/task/2626/fd/4': No such file or directory
du: cannot access `proc/2626/task/2626/fdinfo/4': No such file or directory
du: cannot access `proc/2626/fd/4': No such file or directory
du: cannot access `proc/2626/fdinfo/4': No such file or directory
0       proc
136K    root
8.6M    sbin
4.0K    selinux
4.0K    srv
0       sys
16K     tmp
1.7G    usr
229M    var
0       vmlinuz
```I've ran apt-get clean already, didn't help. I can't figure out how to check trash nor do I know how to check for old kernels in boot directory..:confused: Any assistance would me most appreciated.

---

### Post by oldfred on 2011-11-28
Some more info. Are you using RAID & LVM, I do not know what those may change.

HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
HOWTO: Cleaning up all those unnecessary junk files...
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)
    Caution deborphan will delete anything you manually installed. See comment:
Better to use Synaptic to select the ones you no longer want. Also you get notified about dependencies to be removed and can reconsider, if need be.

#check for large files:
sudo du -h --max-depth=1 / | grep '[0-9]G\>'   # folders larger than 1GB
sudo find / -name '*' -size +1G    # files larger than 1GB
find . -maxdepth 1 -type d ! -name . -exec du -sh '{}' \; | sort -h
dpkg-query -Wf '${Installed-Size}\t${Package}\n' | sort -n
gksudo nautilus /root/.local/share/Trash/files  # Be sure to enable viewing of hidden files.

---

### Post by illuminate1 on 2011-11-28
I appreciate you providing these links and I have tried a few of the suggestions. Still very lost.. For instance, when I try to unmount so I can view only system folders I get the following because I have no space left: 

```
root@server01:/# sudo umount -a
error writing /etc/mtab.tmp: No space left on device
```

I can't download any packages either, get errors due to no space. 

Also, I am using a putty window to log into this server so I do not have GUI access.

---

### Post by drs305 on 2011-11-28
See if you can get just a bit of space by removing cached packages and emptying your trash so you can investigate further:
```
sudo apt-get clean
rm -rf ~/.local/share/Trash
```

---

### Post by illuminate1 on 2011-11-28
The checking for large file suggestions..

```
root@server01:/# sudo du -h --max-depth=1 / | grep '[0-9]G\>'
1.7G    /usr
du: cannot access `/proc/2679/task/2679/fd/4': No such file or directory
du: cannot access `/proc/2679/task/2679/fdinfo/4': No such file or directory
du: cannot access `/proc/2679/fd/4': No such file or directory
du: cannot access `/proc/2679/fdinfo/4': No such file or directory
177G    /backups
126G    /backups2
305G    /
```

```
root@server01:/# sudo find / -name '*' -size +1G
find: `/proc/2653/task/2653/fd/5': No such file or directory
find: `/proc/2653/task/2653/fdinfo/5': No such file or directory
find: `/proc/2653/fd/5': No such file or directory
find: `/proc/2653/fdinfo/5': No such file or directory
/backups/backups/softwareHardware/RADD/radd6000-dvd-sles10-sp3-x64_r1.iso
/backups/backups/softwareHardware/DAC/dac_sles10_with_sp2_dvd_r7_rel1.iso
/backups/backups/softwareHardware/DAC/dac_4_4_r1-b30281.iso
/backups/backups/softwareHardware/DAC/dac_4_3_r2-b29951.iso
/backups/backups/softwareHardware/DAC/dac_4_3_r1-b29643.iso
/backups/backups/softwareHardware/DAC/dac_sles10_with_sp2_dvd_rel4_r1.iso.filepart

```

/backups and /backups2 are mounts to storage devices so I do not think they should be causing the issue, right?

---

### Post by illuminate1 on 2011-11-28
> **drs305 said:**
> See if you can get just a bit of space by removing cached packages and emptying your trash so you can investigate further:
```
sudo apt-get clean
rm -rf ~/.local/share/Trash
```


I've tried both already.. No luck there. :(

---

### Post by synexis on 2011-11-28
--- Removed reply, it was basically a repeat of above posts entered while I was writing mine. ---

---

### Post by drs305 on 2011-11-28
> **illuminate1 said:**
> 
/backups and /backups2 are mounts to storage devices so I do not think they should be causing the issue, right?

Not necessarily. 

This is often the cause of disk space issues. You probably *meant* to backup to another partition but for some reason the partition wasn't mounted at the time of the backup and it was made to your / partition. Unmount any backup partition and then look at /backup and /backups. You will probably find that you have a large amount of data residing there.

---

### Post by illuminate1 on 2011-11-28
> **drs305 said:**
> Not necessarily. 

This is often the cause of disk space issues. You probably *meant* to backup to another partition but for some reason the partition wasn't mounted at the time of the backup and it was made to your / partition. Unmount any backup partition and then look at /backup and /backups. You will probably find that you have a large amount of data residing there.

I had to go into the mtab and fstab to comment out the mounts and reboot, kept getting errors on umount. SO now I look like this: 

```
root@server01# df -H
Filesystem             Size   Used  Avail Use% Mounted on
/dev/cciss/c0d0p1      138G   138G      0 100% /
none                   2.1G   418k   2.1G   1% /dev
none                   2.1G      0   2.1G   0% /dev/shm
none                   2.1G   107k   2.1G   1% /var/run
none                   2.1G      0   2.1G   0% /var/lock
none                   2.1G      0   2.1G   0% /lib/init/rw

```du -s /backups2 shows:
```
root@server01:/backups2# du -s *
131995140       backups

```If I remove the folder "backups", this may resolve my issue? This will not effect any of the data I have on the storage device?

---

### Post by oldfred on 2011-11-28
Were these backups that you need or not. They may be recent or older?

And if this is in /, did it get included in new backups so they are a lot larger?

---

### Post by illuminate1 on 2011-11-28
> **oldfred said:**
> Were these backups that you need or not. They may be recent or older?

And if this is in /, did it get included in new backups so they are a lot larger?


Well I went and asked the boss man about the files left over in this location (he's been making the copies) and he felt it safe to delete them. / is now down to 2%! Thank you all so much for your help!

---

