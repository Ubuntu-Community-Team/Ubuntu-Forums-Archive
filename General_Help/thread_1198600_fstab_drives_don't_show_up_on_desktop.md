---
title: "fstab drives don't show up on desktop?"
date: 2009-06-27
forum: General Help
---

### Post by thecheeks on 2009-06-27
So this is a new problem... just reformatted and now none of my internals mounted with fstab show up on the Desktop. They show up at the mount points though. 

I checked gconf for Natualis (sp) and Show Volumes is ticked.

---

### Post by drs305 on 2009-06-27
Please post the results of:
```
sudo blkid -c /dev/null  # display UUIDs
cat /etc/fstab  # display fstab
mount  # show where things are currently mounted

```

---

### Post by thecheeks on 2009-06-27
> **drs305 said:**
> Please post the results of:
```
sudo blkid -c /dev/null  # display UUIDs
cat /etc/fstab  # display fstab
mount  # show where things are currently mounted

```

/dev/sda1: UUID="62A447BEA4479387" TYPE="ntfs" 
/dev/sda5: UUID="24ca6c9e-c782-4143-bfaa-0fb4749d9bf6" TYPE="ext3" 
/dev/sda6: UUID="ceff6dbe-9dc9-447b-8653-e43b876e9b86" TYPE="swap" 
/dev/sdb1: UUID="fd165b39-d75d-4894-be06-670f388e8602" TYPE="ext3" 
/dev/sdc1: UUID="21fc7cf9-916d-49b7-8b01-6e0c980223da" TYPE="ext3" 
/dev/sdd1: LABEL="Music" UUID="06c90094-fc31-413d-bb67-fb2261fb1526" TYPE="ext3"



# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=24ca6c9e-c782-4143-bfaa-0fb4749d9bf6 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=ceff6dbe-9dc9-447b-8653-e43b876e9b86 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb1	/Media	ext3	defaults	0	0
/dev/sdc1	/Music	ext3	defaults	0	0




/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-14-generic/volatile type tmpfs (rw,mode=755)
/dev/sdb1 on /Media type ext3 (rw)
/dev/sdc1 on /Music type ext3 (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/thecheeks/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=thecheeks)
/dev/sdd1 on /media/Music type ext3 (rw,nosuid,nodev,uhelper=hal)




Now to find out what silly little mistake I've made :) SDD1 is just an external harddrive, transferring some stuff over real quick incase that looks weird since it's not in the fstab.

---

### Post by drs305 on 2009-06-27
Partitions mounted in /media show up on the Desktop. Your partitions aren't really mounted in /media they are mounted on / *as* **Media** and **Music**. There is a difference. If you made the mount points and mounted them to /media/Media and /media/Music2, you would see them on your desktop.

You do have sdd1 mounted on /media/Music, so you should be able to see that one and be careful where you mount the other *Music* partition. If you have the fstab entry (sdc1) mount to /media/Music, sdd1 would probably mount to "Music-1" since it isn't listed in fstab but appears to be automounting.

---

### Post by thecheeks on 2009-06-27
> **drs305 said:**
> Partitions mounted in /media show up on the Desktop. Your partitions aren't really mounted in /media they are mounted on / *as* **Media** and **Music**. There is a difference. If you made the mount points and mounted them to /media/Media and /media/Music2, you would see them on your desktop.

You do have sdd1 mounted on /media/Music, so you should be able to see that one and be careful where you mount the other *Music* partition. If you have the fstab entry (sdc1) mount to /media/Music, sdd1 would probably mount to "Music-1" since it isn't listed in fstab but appears to be automounting.

Well that makes sense... sort of. Last week, before I reformatted, I had them mounted at /Media and /Music also, the same configuration, and they showed up on the desktop. A fluke maybe? Is there anyway to have them at those points and still show up on the desktop? It's just easier for me to remember they're there but if I need to change mounts I will.

---

### Post by drs305 on 2009-06-27
> **thecheeks said:**
> Well that makes sense... sort of. Last week, before I reformatted, I had them mounted at /Media and /Music also, the same configuration, and they showed up on the desktop. A fluke maybe? Is there anyway to have them at those points and still show up on the desktop? It's just easier for me to remember they're there but if I need to change mounts I will.

I wondered about that. I don't really believe in flukes. The first thing that came to mind was that you had made a link (which you can do again) to the Desktop for each of the partitions. ( ln -s /Music $HOME/Desktop ). A soft link would have had the link symbol on it which you probably would have remembered, but it is one way it could have happened.

---

### Post by thecheeks on 2009-06-27
> **drs305 said:**
> I wondered about that. I don't really believe in flukes. The first thing that came to mind was that you had made a link (which you can do again) to the Desktop for each of the partitions. ( ln -s /Music $HOME/Desktop ). A soft link would have had the link symbol on it which you probably would have remembered, but it is one way it could have happened.

Nah no link because when I unplugged the drives they just wouldn't be on the desktop. A link would still be there with a red X.

Odd. I'll just remount them to /media then to save headaches.

---

