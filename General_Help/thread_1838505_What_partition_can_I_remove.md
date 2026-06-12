---
title: "What partition can I remove?"
date: 2011-09-03
forum: General Help
---

### Post by madebyjordan on 2011-09-03
Hey guys,

Shortened version of a long story - I botched an upgrade to 11.10 beta and I partitioned my HD, reinstalled 11.04 and cp'd files from the old broken partition to the new 11.04 one.

Can I double check before I do this that I'm deleting the right partition (the older partition with broken 11.10)?

[[IMG]http://img820.imageshack.us/img820/5952/selection018v.png[/IMG]](http://imageshack.us/photo/my-images/820/selection018v.png/)

Many thanks in advance,
Jordan

---

### Post by garvinrick4 on 2011-09-03
You can boot into the 11.04?
run in a terminal.
```
df -h
```That will tell you what partition you are in.

And in Gparted the one with the key is the one you are in.
You cannot work on any partition that is in use (mounted)

Get rid of the extra swap also.

While in your choosen install before you touch anything make sure grub is in mbr from right install.
```
sudo grub-install /dev/sda
``````
sudo update-grub
```

---

### Post by garvinrick4 on 2011-09-03
Getting rid of sda1 will make it look a bit sloppy, can you back up your /home in
sda6 and just format drive and do fresh install so you will start from beginning of
drive instead of middle. Or you can put another install in sda1 of linux and have
a dual boot. Just choose to do it manual in installer (ubiquity) and choose sda1 to
install with no swap (already have one). Lots of different ways to clean up drive, consider
what you would like to do.
format is ext4
mount point is  /

---

