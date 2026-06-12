---
title: "Right kick mount ISO's ?"
date: 2010-05-13
forum: General Help
---

### Post by morepowerr on 2010-05-13
I am sorry to take up people time with this. I am sure It is something EZ. But I just can remember how to do it off hand.

 Doe's any one know the right command to put in "open with". To lent me mount any .iso

 I tried using "mount -o loop -t iso9660  /media/iso" but that didn't work out. :(

 Thanks for any help.

---

### Post by quixote on 2010-05-15
I'm not sure you need to specify the filesystem (the -t iso9660 part).  And if you specify a mount point (/media/iso) there has to be a directory already made in /media by that name.```
sudo mkdir /media/iso
```

I think you have to run the mount command as sudo.  If you don't specify a mountpoint, as in the example below, then I think it defaults to /media/cdrom.  However, if it doesn't, then just make a dir, like /media/iso and specify it.
```
sudo mount -o loop */path/to/the-downloaded*.iso
```There's more detail [here]("https://help.ubuntu.com/community/MountIso#Mounting%20ISO%20Files").  Any media mounted in the /media directory should appear on the desktop.

---

### Post by WinterRain on 2010-05-15
Or, if you prefer GUI method, install Gmountiso.

---

### Post by gadolinio on 2010-05-15
> **WinterRain said:**
> Or, if you prefer GUI method, install Gmountiso.
I've used it successfully, but it doesn't recognize the iso file sometimes. Don't know why.



> **quixote said:**
> if you specify a mount point (/media/iso) there has to be a directory already made in /media by that name.

> **quixote said:**
> 
I think you have to run the mount command as sudo.

+1

---

### Post by morepowerr on 2010-05-15
Thanks for all the answers. I know about command line mount. But was really hopeful there was a way to do it from "open with" in nautilus.

 (AkA)  Right click on any.iso file in nautilus. 

 I have been able to get it to work with "Archive Mounter" ( /usr/lib/gvfs/gvfsd-archive )

 But the second I try to run any thing on the ISO, it un-mounts!

 When I check my logs I get the below error when it un-mounts.

 kernel: [147264.975171] gvfsd-archive[8208]: segfault at 14 ip 08055825 sp bf8cc780 error 4 in gvfsd-archive[8048000+1d000]

Thanks

---

