---
title: "Mounting ext3 filesystem from dual boot."
date: 2006-04-26
forum: General Help
---

### Post by echo $USER on 2006-04-26
Waht do I need to put in my /etc/fstab to automount a ext3 filesystem on a dual boot partition?  I have fedora 4 on hda1, and ubuntu on hda3.  I only want to read and execute from it (media files).  Thanks

---

### Post by jazzmuzik on 2006-04-26
You know that your media exists on partition hda1. So next create a mount point for it in Ubuntu:

Something like this:

sudo mkdir /media/mymedia

Then add a line to /etc/fstab like this:

```
/dev/hda1       /media/mymedia         ext3    defaults        0       2
```

Now you're ready to mount the drive:

mount /dev/hda1

Or unmount it with: 

umount /dev/hda1

Because you created the line in /etc/fstab that drive will be mounted and available every time you boot up.

---

### Post by AndyCooll on 2006-04-26
Try this:

```
sudo mkdir /media/fedora
```

```
sudo gedit /etc/fstab
```

Then add the following line:
```
/dev/hda1 /media/fedora ext3 defaults 0 2
```

```
sudo mount -a
```

You don't have to create the directory in /media you can of course create a directory anywhere you want. You can also call it what you like.

:cool:

---

### Post by ajgreeny on 2006-04-26
First you need to make a folder in which to mount your fedora partition by entering:-
*sudo mdir /media/fedora*
You then need to add the line:-
/dev/hda1       /media/fedora	ext3   defaults	0	2
to your /etc/fstab file.  Then do a *sudo mount -a* and all entries in your fstab should mount.

---

### Post by mentallysilent on 2006-04-26
something like this might do it:

/dev/hda#         <mount point>        ext3       defaults,user      0  0

where you replace # with the partition number you need to mount and <mount point> with the location you need it mounted. You could create a directory under /media and have that as your mount point. Hope this helps.

---

### Post by echo $USER on 2006-04-26
Nice, all is well now; no need to duplicate my media.  Thanks for all the replies.

---

### Post by jazzmuzik on 2006-04-26
Generally you never want to duplicate media. Management of the data becomes insane otherwise.

---

