---
title: "rhythmbox error in ubuntu jaunty"
date: 2009-09-14
forum: General Help
---

### Post by macjorgen on 2009-09-14
Hi!

I have been using rhythmbox for a while and i'm loving it. It's really good to have a music player that can import and export tracks from ipod to computer and vice versa. to my knowledge rhythmbox is the only program that does that (?). The one thing i always hated about itunes was that you could never import tracks from your ipod to your computer, rhythmbox does that! 
however, i recently upgraded to ubuntu jaunty 9.04 and rhythmbox is giving me an error:


Error transferring track

Error creating directory: Permission denied


does anyone know what to do, it's doing my head in??

cheers
macj.

---

### Post by sanguinoso on 2009-09-14
Is the error when attempting to transfer a track to the iPod? Or on the hard drive. The iPod could be mounted read only, and the hard drive could have a permissions problem. The command mount shows the mount options for all drives. 'ls -al' will show you if the directory on the hard drive has a permissions error.

---

### Post by macjorgen on 2009-09-14
hi!
the error is when i attempt to transfer to the ipod. no errors transferring from ipod to computer. if so, how do i change the i not to be read-only??

cheers
macj

---

### Post by sanguinoso on 2009-09-14
Can you post the output of the mount command?


A bunch of lines that look line this

/dev/sr0 on /media/cdrom1 type iso9660 (ro,nosuid,nodev,utf8,user=root)

---

### Post by macjorgen on 2009-09-14
sorry, can you please show me the command to put?

macj

---

### Post by mr.suchy on 2009-09-14
```
sudo mcview /etc/fstab
```

---

### Post by macjorgen on 2009-09-14
hi!

this is what i get after typing:

jorgen@jorgen-desktop:~$ sudo mcview /etc/fstab
sudo: mcview: command not found

---

### Post by sanguinoso on 2009-09-14
```
mount
```

---

### Post by macjorgen on 2009-09-14
jorgen@jorgen-desktop:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/jorgen/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jorgen)
/dev/sdc1 on /media/J?GGA'S IPO type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/sdd1 on /media/MISC type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)

---

### Post by sanguinoso on 2009-09-14
Hm that shows that the ipod is mounted rw (read write). I'm kind of lost as well. One thing you could try is a reinstall of rhythmbox in case the config files got messed up during the upgrade.

```
sudo apt-get remove rhythmbox --purge
sudo apt-get install rhythmbox

```

---

### Post by macjorgen on 2009-09-14
hi!

i tried reinstalling but got the same message. don't know myself, it works fine in ubuntu 8.10.
thanks anyway, appreciate it

cheers
macj

---

### Post by macjorgen on 2009-11-15
Hi, it's taken a while!

I finally found the solution to my problem. I had to reformat the iPod using iTunes. It seemed like the software on the iPod was too old. Reinstalled it and works like a charm...

Thanx
MacJ

---

### Post by yichuan on 2010-04-11
I'm not totally sure about this, but I have exactly the same problem.

I think the reason is when ipod get connect, it was treated as root. So even if it has rights to read and write, rhythmbox as a user program will unable to perform write action.

Ok my problem get solved by magic...I don't know if the problem will come up again. What I did is try to reconnect ipod to rhythmbox few times, try to eject ipod few times and try to sudo rhythmbox in the command line. After few trial, I'm able to transfer sound to ipod now. Wield...

---

### Post by yichuan on 2010-04-11
Ok my problem get solved by magic...I don't know if the problem will come up again. What I did is try to reconnect ipod to rhythmbox few times, try to eject ipod few times and try to sudo rhythmbox in the command line. After few trial, I'm able to transfer sound to ipod now. Wield...

---

### Post by sanguinoso on 2010-05-27
If you mark this thread as solved it will be helpful to others.

---

