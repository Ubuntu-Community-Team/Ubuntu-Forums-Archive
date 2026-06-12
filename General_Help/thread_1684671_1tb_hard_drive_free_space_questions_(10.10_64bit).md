---
title: "1tb hard drive free space questions (10.10 64bit)"
date: 2011-02-09
forum: General Help
---

### Post by techno-mole on 2011-02-09
Evening all.

I have a small issue with a 1tb sata drive I've just instlled.

It was brand new, and I've install maverick 64bit on it, now I'm a little puzzled about the amount of free space there is on the drive.

If I open nautilus it shows the amount of free space in the bottom left section of the screen (see picture-1)
This seems a little odd to me, where the hell has all the space gone ? my entire home directory is a total of 40.3gb (see picture-2)

I've done some looking about and I can't seem to find out where the space has gone, I had a look at the drive using gparted and this is what I got (see picture-3)

If you look at the pictures it seems I'm missing about 320 gb or so, any guesses to where the hell it's gone ? I would appreciate any pointers.

---

### Post by Neezer on 2011-02-09
try 
df -a

and post the output of that....

EDIT:

You can also use the disk usage analyzer. It is under Applications -> Accessories
this tool is quite helpful as well....sometimes you have things in the hidden trash files that can add up.

---

### Post by bryanl on 2011-02-09
use tune2fs to find out about reserved space.

When an ext file system is created, 5% is reserved for system use. With large drives, that can add up to a lot of space that you won't see as available on the partition. (50GB per TB)

For partitions that don't have any system files and don't have to worry about what happens if it fills up, tune2fs -m 0 will free up the space. (see man tune2fs)

---

### Post by techno-mole on 2011-02-09
Thanks for the help, I've figured out what it was.

I've been running photorec on an external drive to recover some lost files, because it runs as root, when I'd gone through the folders it created to search for files and then deleted those folders they hadn't deleted they'd gone into a trash file in the root directory.

I ran nautilus as root and emptied the folder and all of a sudden my 300gb came back.

Thanks again for the help, much appreciated.

---

