---
title: "empty ~/.gvfs"
date: 2009-11-15
forum: General Help
---

### Post by W. Irving on 2009-11-15
After upgrading to karmic, the .gvfs dir is always empty. In 8.04 it used to contain any mounted network share (and, IIRC, devices like the DVD and USB memories).
As I use Unison (which operates only on local paths) I really need this functionality.

The daemon is obviously alive..
```

elias@trotsky:~$ mount | grep gvfs
gvfs-fuse-daemon on /home/elias/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=elias)
elias@trotsky:~$ ps -A -o command | grep gvfs
/usr/lib/gvfs/gvfsd
/usr/lib/gvfs//gvfs-fuse-daemon /home/elias/.gvfs
/usr/lib/gvfs/gvfsd-trash --spawner :1.9 /org/gtk/gvfs/exec_spaw/0
/usr/lib/gvfs/gvfs-gdu-volume-monitor
/usr/lib/gvfs/gvfs-gphoto2-volume-monitor
/usr/lib/gvfs/gvfsd-burn --spawner :1.9 /org/gtk/gvfs/exec_spaw/1
/usr/lib/gvfs/gvfsd-metadata
/usr/lib/gvfs/gvfsd
/usr/lib/gvfs/gvfsd-trash --spawner :1.8 /org/gtk/gvfs/exec_spaw/0
/usr/lib/gvfs/gvfs-gdu-volume-monitor
/usr/lib/gvfs/gvfs-gphoto2-volume-monitor
/usr/lib/gvfs/gvfsd-burn --spawner :1.8 /org/gtk/gvfs/exec_spaw/1
/usr/lib/gvfs/gvfsd-metadata
/usr/lib/gvfs/gvfsd-computer --spawner :1.8 /org/gtk/gvfs/exec_spaw/3
/usr/lib/gvfs/gvfsd-smb --spawner :1.8 /org/gtk/gvfs/exec_spaw/4
/usr/lib/gvfs/gvfsd-smb-browse --spawner :1.8 /org/gtk/gvfs/exec_spaw/5

```

..and while all the mounting works just as before, ~/.gvfs remains empty.

Open to, and grateful for, suggestions! :neutral:


UPDATE: A reboot later, and the thing works as it's supposed to. It's like Windows!

---

### Post by pigphish on 2009-11-19
its there... it's just hidden. I would check but I seem to be having a different gvfs problem

---

### Post by W. Irving on 2009-12-08
I had problems with this again. ~/.gvfs remained empty although I'd opened a network directory. Googled and saw mentions of a permissions problem. .gvfs is rwx for the user only. Solution was to
```
$ umount ~/.gvfs
```

then

```
$ chmod 755 ~/.gvfs
```

and finally

```
$ /usr/lib/gvfs/gvfs-fuse-daemon ~/.gvfs
```

After that the dir reflects what is mounted through fuse.
Hopefully this'll help someone else in the future.

---

### Post by paxmark1 on 2010-01-08
Wow, gotta be careful with that chmod -R 
Thanks for the tip.

---

### Post by quillerszasza on 2012-07-30
Ah, thank you kind Sir for this precious post! I am setting up samba shares on my RasPi device and I couldn't stream videos to VLC.  ~/.gvfs was the answer, though I have no idea, what the hell is this :-D
Anyway, it works ...

---

### Post by wildmanne39 on 2012-07-30
Hi, this is an old thread so it has been closed please start a new thread of your own with a descriptive title. 
Thanks

---

