---
title: "Change owner from root on NTFS filesystem"
date: 2011-02-04
forum: General Help
---

### Post by TheCosmicFrog on 2011-02-04
Hi everyone,

I use a mounted NTFS filesystem as my main data storage drive. I then symlink all my Windows folders (Documents, Pictures, etc.) into my Ubuntu home folder. Works great, because it means I can share files between Windows and Ubuntu hassle-free.

However, any file created on or saved to the NTFS partition automatically has its owner set as "root". Is it possible to set the default owner to me (aaron)? Or does it have to be root on NTFS?

Screenshot below:
[IMG]http://i173.photobucket.com/albums/w53/CZMQFRG/Screenshot-19.png[/IMG]

Thanks guys!

---

### Post by Tyggna on 2011-02-04
You're gonna want to try mounting the ntfs partition in your user space.  
The reason it's stuck in root is because root is the one using the ntfs-3g driver to mount it, and that usually has to be done in root-user space.

if you unmount the volume as root, and then type```
ntfs-3g /dev/sda# /path/to/mount
``` as your user, then everything will show as being owned by you--I believe.

This, in the larger picture, is kinda a silly thing to do though.  Whoever "owns" the file is simply the one who gets to set the permissions on it.  In a sense, root owns everything--and when it gains ownership of your ntfs volume on boot, it grants full access to it to everyone who wants it.

You can make yourself owner of it--but all it might do is change the name of the owner to you.  NTFS doesn't support linux file permissions, so you can't change them.

---

### Post by TheCosmicFrog on 2011-02-04
Thanks for the response, Tyggna. The way it's set up at the moment is through the fstab file, so I'm guessing that's why everything is set up as root by default. Is keeping everything on the NTFS filesystem a serious security risk? I can't think of any "neater" way to share files between both operating systems.

---

### Post by psusi on 2011-02-04
If you mount it with fstab then you need to specify who the owner is with the uid= mount option.

---

