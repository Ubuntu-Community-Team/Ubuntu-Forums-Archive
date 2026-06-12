---
title: "making the most of a small SSD"
date: 2010-11-11
forum: General Help
---

### Post by DatBugler on 2010-11-11
I will soon be upgrading to a new system, which will have a large hard disk for /home and a 40G or 60G SDD for the OS. I'm thinking there are a few other things I'd like to put on the SSD for launch speed, like some of the subdirectories of my Documents folder, and my WINE programs. Is there a nice way I can selectively put things from /home on the SSD instead of the hard drive? The only thing that I can think of is, for example, to create a separate /home/me/Documents partition on the SSD. That seems really yucky though. Suggestions?

---

### Post by sanderd17 on 2010-11-11
If you don't want to make different partitions, you can work with symlinks.

Do you have experience with command line?

if so, just use 

```

man ln

```

to see how it works. 

you need to use the -s option so have a symbolic link, otherwise, it will be a hard link, some kind of synhronised copy.

Links are not that elegant option, but you need to choose one of the two: partitioning or linking. For bigger directories, partitions are advised, for smaller, links are advised.

Edit: before you start fuddeling with links or partitions, try the normal configuration and see if you're happy with it or not. See if it takes too long to open a document or not.

---

### Post by DatBugler on 2010-11-11
Yuck, symlinks are even less nice than partitions. I've tried just what you suggested on a previous system, and it caused problems because some programs expected an actual directory at a certain place, and choked when they found a symlink instead.

---

### Post by sanderd17 on 2010-11-11
> **DatBugler said:**
> Yuck, symlinks are even less nice than partitions. I've tried just what you suggested on a previous system, and it caused problems because some programs expected an actual directory at a certain place, and choked when they found a symlink instead.

huh? symlinks should work just fine, the only problem you can have with them is the maintenance of the system. When you use a lot of symlinks, you can get in trouble with links linking to other links and creating a loop.

can you do a 

```

ls -al

```

of the directory where your symlink is and one of the directory where you link to?

---

