---
title: "rsync help"
date: 2010-05-08
forum: General Help
---

### Post by AnalBeard on 2010-05-08
I have a fairly simple request (well i think it is), which i'm kinda stuck on. My server is headless and boots off a compactflash card. I have a secondary CF card purely to back up the primary card to in case it were to fail (due to shorter lifespan than hdds etc). The idea with the backup is to use rsync to perform an incremental backup at a certain invterval, meaning that the backup will never be particularly old and i can just swap cards and carry on.

the problem is this: i can set rsync up to mirror a drive (using an exclude list for /var etc), but how can i get it to back up /boot etc? has anyone tried this before? obviously this idea also entails backing up grub etc. any help is appreciated!

---

### Post by ridetheteapot on 2010-05-08
if you want everything mbr, partition table why not just use dd to just copy the whole file system over?

if you HAVE to exclude specific folders/files - maybe first clone the drives partition table, use dd & md5sum to check for mbr/table changes and update (overwrite) appropriately, and rsync to back up partition contents. could be a pretty simple script but maybe there are other solutions

---

### Post by AnalBeard on 2010-05-09
Ok, so i've never used dd before, i presume from doing a bit of reading that it will result in a mirror image of the boot drive with each partition intact etc? 

i only suggested rsync as once it's cloned /boot won't be altered, it'll only be changes to the filesystem which need to be made.

---

### Post by jerome1232 on 2010-05-09
The problem with dd is you'll have to take the server offline to do it. You can use raid or lvm2 to mirror volumes. It would be a better solution than an rsync script or taking the server down periodically to run dd imo.

---

### Post by AnalBeard on 2010-05-09
Hmm, i hadn't thought of using a raid1 setup, would that also mirror the partition scheme?

i wouldn't plan on using dd to mirror everytime, i'd only be setting up the duplicate drive with that initially and then using rsync (or some similar method) from then on to keep the filesystem up to date with incremental updates.

---

