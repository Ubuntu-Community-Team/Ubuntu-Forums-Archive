---
title: "Bin Folder Deleted"
date: 2010-05-29
forum: General Help
---

### Post by Onisutra on 2010-05-29
I made the unfortunate mistake of doing this (sudo rm -r /bin) instead of (sudo rm -r bin) in the folder I was in..I'm trying to copy my data over from my Karmic system using mount, but I'm unable to mount. When I try to mount I get errors of an wrong fs type.. I've done fdisk -l & I get this

/dev/sda1   *           1       37599   302013936   83  Linux

What the heck filesystem is Linux? Is that like ext3 or something? I don't know.

Here is what I'm trying to run
mount -t ??? /dev/sda1 /media/disk -o force

Also, besides that. If there a way I can fix my OS without having to do a reinstall? Or at least is there a way can backup my files? I have a 1tb external so that's not the issue.. 

Any help is appreciated.

---

### Post by wojox on 2010-05-29
Your unable to mount because that command was in the /bin directory. You could try a LiveCD.

---

### Post by bildr on 2010-05-29
fix without reinstall, i can't help you there.

generic linux partition is ext3, but ext4 and 3 are both backwards compatible so you could even mount is as ext2 you would be able to read files.

and yes, i assumed you were already on a recovery cd

---

### Post by Onisutra on 2010-05-30
> **wojox said:**
> Your unable to mount because that command was in the /bin directory. You could try a LiveCD.

I was using the live cd.

---

### Post by wojox on 2010-05-30
Just try:

```
sudo mount /dev/sda1 /mnt
```

---

### Post by Onisutra on 2010-05-30
> **wojox said:**
> Just try:

```
sudo mount /dev/sda1 /mnt
```

It asks for the file system type. I enter ext3 and nothing.

---

