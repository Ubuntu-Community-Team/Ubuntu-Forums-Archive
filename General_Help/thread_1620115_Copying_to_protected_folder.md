---
title: "Copying to protected folder"
date: 2010-11-12
forum: General Help
---

### Post by adhika on 2010-11-12
Hi,

I am trying to copy a (custom XML) file to a protected folder (namely /usr/share/games/FlightGear/Protocol) for data Input/Output.

I tried copying and pasting the folders and it doesn't work. I realized that it is because only root user has the permission to do modification.

So, I tried using "sudo cp" to copy the file. The file was copied, but the content now becomes unreadable when I tried to open the file. 

Can somebody advises me on how to do this properly?

I am running the Maverick.

Thanks!

---

### Post by AlphaLexman on 2010-11-12
post the output of:```
mount
```

---

### Post by adhika on 2010-11-12
The output from executing mount is as follows:
```
/dev/sda5 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/adhika/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=adhika)
/dev/sda1 on /media/SQ004855P05 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)

```

---

### Post by adhika on 2010-11-13
Any clue on this one?

---

### Post by mister_playboy on 2010-11-14
> **adhika said:**
> I tried copying and pasting the folders and it doesn't work. I realized that it is because only root user has the permission to do modification.

You can run Nautilus as root to do this:
```
gksudo nautilus
```
Not sure if it will solve your problem of the file becoming unreadable, but it's convenient to know anyway.

---

### Post by Swagman on 2010-11-14
> **mister_playboy said:**
> You can run Nautilus as root to do this:
```
gksudo nautilus
```
Not sure if it will solve your problem of the file becoming unreadable, but it's convenient to know anyway.

^ This

Plus "My Bad"

I was going to say sudo nautilus but you reminded me is gksudo nautilus

---

### Post by adhika on 2010-11-14
Hi all,
```

gksudo nautilus

```

works fine to browse the file. But if I call the function from some other application (e.g. my own C file) then it doesn't work.

I found this to be working though:
```

gksudo gedit

```

Copy/Paste the content of the file to the editor and save it. It will be readable although you are not in the "sudo nautilus" mode.

---

