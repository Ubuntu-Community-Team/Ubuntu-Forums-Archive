---
title: "how to do a manual installation"
date: 2009-10-10
forum: General Help
---

### Post by bigdee973 on 2009-10-10
i need to know how to do a manual installation so i could install ext4.  but the thing is that its confusing.  could someone send me a link or explain what to do step by step.

---

### Post by nikhilbhardwaj on 2009-10-10
why are you trying to install ext4
ext4 is a filesystem

do you have ubuntu installed already
if so then re-installing just to get ext4 isn't recommended by me

if not then when you partition your disks
choose ext4 as the filesystem

but if you don't know about the differences between ext3 and ext4 and don't have a good reason to install ext4 
i'd suggest that you dont try it

---

### Post by bigdee973 on 2009-10-10
> **nikhilbhardwaj said:**
> why are you trying to install ext4
ext4 is a filesystem

do you have ubuntu installed already
if so then re-installing just to get ext4 isn't recommended by me

if not then when you partition your disks
choose ext4 as the filesystem

but if you don't know about the differences between ext3 and ext4 and don't have a good reason to install ext4 
i'd suggest that you dont try it

no good reason? ext4 is fast. i know its a filesystem and i want my partition to be formatted in ext4 because of the quick speed it offers.  i would just like to know how to do a manual install

---

### Post by sisco311 on 2009-10-10
> **bigdee973 said:**
> no good reason? ext4 is fast. i know its a filesystem and i want my partition to be formatted in ext4 because of the quick speed it offers.  i would just like to know how to do a manual install

Not exactly what are you looking for, but this guide should give you a general idea of how to manually partition during the installation:

[http://psychocats.net/ubuntu/installseparatehome]("http://psychocats.net/ubuntu/installseparatehome")

---

### Post by nikhilbhardwaj on 2009-10-10
> **bigdee973 said:**
> no good reason? ext4 is fast. i know its a filesystem and i want my partition to be formatted in ext4 because of the quick speed it offers.  i would just like to know how to do a manual install

ok
boot of the live cd
start the installation
at the time when it asks you to parttion donot choose automatic mode
choose custom
there you can specify ext4 as the filesystem

make sure to create a swap partition too
just in case

nut ext4 isn't as fast as you seem to thing
the performance gains are marginal
i've found xfs better in terms of speed

---

### Post by bigdee973 on 2009-10-10
> **nikhilbhardwaj said:**
> ok
boot of the live cd
start the installation
at the time when it asks you to parttion donot choose automatic mode
choose custom
there you can specify ext4 as the filesystem

make sure to create a swap partition too
just in case

nut ext4 isn't as fast as you seem to thing
the performance gains are marginal
i've found xfs better in terms of speed

you see my problem is creating that parition.  ive attempted plenty of times to do a manual installation but the configuration is what confuses what would i have to put..theres always this option of creating root with manual install..i dont know what to do..or what directory to create

---

### Post by bigdee973 on 2009-10-10
> **sisco311 said:**
> Not exactly what are you looking for, but this guide should give you a general idea of how to manually partition during the installation:

[http://psychocats.net/ubuntu/installseparatehome]("http://psychocats.net/ubuntu/installseparatehome")

thanks dude i think this is extactly what i need.  ill update you to see if i installed ubuntu with ext4 successfully.

---

### Post by falconindy on 2009-10-10
Manually installing software requires magnetized needles and a steady hand...

Joking aside, its easy to specify the partitions yourself. When the partition manager loads up, you'll see section(s) labelled free space. Identify the free space where you'll be installing Ubuntu, and create a new partition in that space. You'll specify "Primary" and "Ext4" as the partition type, ideally at the beginning of the segment, and then for the mount point, type "/" (without the quotes, of course).

You can go on and create other partitions, mounting them at /home or /usr/local, but you don't need to. The only requirement is mounting a partition at root. It's also recommended that declare a swap partition.

When you're done, you'll have something like this:
[IMG]http://www.serenux.com/~hyrax/snaps/UbuntuJauntyManuallyPartition2.png[/IMG]

---

### Post by nikhilbhardwaj on 2009-10-10
you need a minimum of two directories when installing manually
/  for holding everything
and a swap partition(roughly twice your main memory size)
choose ext4 as the filesystem for /

you should however create partitions for 
/home
and
/boot
too but / and swap is the bare minimum

---

