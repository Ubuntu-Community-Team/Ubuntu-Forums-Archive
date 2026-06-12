---
title: "Mount /home in RAM"
date: 2010-11-13
forum: General Help
---

### Post by mooreted on 2010-11-13
Just playing around with things for the heck of it.

I would like to mount my home directory in a ramdisk. I have tried:

mount --bind /home/mooreted /dev/shm

But not sure if that's actually running home in RAM.

---

### Post by blueridgedog on 2010-11-13
Since you need a /home to log in, you would need to create a ramdisk then copy the contents to it, then unmount your existing home and remount the new ramdisk at /home.

The first four results have have merit:

[http://www.google.com/search?sourceid=chrome&ie=UTF-8&q=mount+/home+ramdisk](http://www.google.com/search?sourceid=chrome&ie=UTF-8&q=mount+/home+ramdisk)

---

### Post by mooreted on 2010-11-13
Hmm, I thought /dev/shm already was a dynamic ramdisk.

---

### Post by blueridgedog on 2010-11-13
You can use /dev/shm, but it would be cleaner to create what you want.  However, even if you use /dev/shm, you sill would need to mount it, copy home files to it, then unmount it so that it can be remounted as /home.  If I were trying to create such a setup, I would start from scratch as there may be other tools that use /dev/shm.

---

### Post by mooreted on 2010-11-13
> **blueridgedog said:**
> You can use /dev/shm, but it would be cleaner to create what you want.  However, even if you use /dev/shm, you sill would need to mount it, copy home files to it, then unmount it so that it can be remounted as /home.  If I were trying to create such a setup, I would start from scratch as there may be other tools that use /dev/shm.

Ah, I see. Ok, I think I have the krux of the matter from the first link. Don't need any of the truecrypt procedure. 

Thanks for the help.

---

### Post by mooreted on 2010-11-14
Okay, that works. I just had to modify the following to meet my own needs:

create tmpfs

modify /etc/fstab
$ su -
# echo "none /tmp tmpfs defaults,size=128M 0 0" >> /etc/fstab
# echo "none /home tmpfs defaults,size=512M,mode=1777 0 0" >> /etc/fstab

truecrypt prompt to load your /home at each gnome start

add (just under first comments) into /etc/gdm/Init/Default
(replace /dev/sda3 by your data partition) :
# mount truecrypt
truecrypt /dev/sda3 /media/truecrypt1

# load /home
cp -r /media/truecrypt1/savehome/* /home

# umount truecrypt
truecrypt -d /dev/sda3

# chown
for user in $(ls /home); do
    chown -r $user:$user /home/$user 
done

---

