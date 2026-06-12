---
title: "converting from ext3 to reiserfs?"
date: 2006-06-21
forum: General Help
---

### Post by nanotube on 2006-06-21
So, after seeing how easy it is to recover accidentally deleted files from reiserfs (and knowing how impossible it is with ext3) (cf [http://ubuntuforums.org/showthread.php?t=200245)](http://ubuntuforums.org/showthread.php?t=200245)), i got to thinking that i want to change my ubuntu partition from ext3 to reiserfs. so, what i am thinking to do is the following. 
1. boot from a livecd
2. copy all the stuff from my ubuntu / partition (i only have one solid 9 gig partition for ubuntu (plus a swap, of course)) to the free space on my fat32 data drive
3. format the ubuntu partition into reiserfs (possibly, even split it into two partitions, one for /, one for /home)
4. restore all the stuff i have copied over back onto the newly-formatted reiserfs partition.

so my questions are as follows:
1. will this work, generally speaking, or is this a really bad idea? as in, if i copy all files, using some method or other, then copy them back, am i going to still have a bootable system?
2. what's the best way to copy the entire contents of ubuntu / onto fat32? (keeping in mind that the if the files are just copied, the permissions will get screwed up, since fat32 doesn't support permissions). once stuff is copied, of course, what's the best way to restore the original stuff?
3. anything else i am missing?

note: this is on breezy, but i figure the partitions and all such underlying system things will not have changed between breezy and dapper (or for that matter, between any linux distro ;) ), so i'm posting in the dapper section because it is more active nowadays.

---

### Post by aysiu on 2006-06-21
Maybe [this](http://ubuntuforums.org/showthread.php?t=81311) would work.

---

### Post by nanotube on 2006-06-21
[QUOTE=aysiu]Maybe [this](http://ubuntuforums.org/showthread.php?t=81311) would work.[/QUOTE]
hmm, maybe it would. seems like a good thing to try. thanks :)

---

### Post by thasheep on 2006-06-21
I've done similar things (converting between filesystems) using tar and it has worked well. I was about to explain how to do it but that link is a good guide (In fact I think I followed it or something very like it the first time I tried). If you have the space on your vfat drive, it'd probably be faster to leave out the compression entirely.
Boot off any linux live/rescue cd and find a terminal. Here're the commands I'd use
```
sudo -i # only needed if you're not already root
mkdir /mnt/fat /mnt/ubuntu
mount /dev/hda4 /mnt/ubuntu  # change to actual partition
mount /dev/hda5 /mnt/fat       # "
cd /mnt/ubuntu
tar -cpvf /mnt/fat/ubackup.tar .   # make sure its a ".", not "/"
### you don't need to worry about excluding proc, sys, dev because ###
### that only applies to the current root filesystem. Here it's mounted ###
### at /mnt/ubuntu, not /  ###
### Make sure that step works before going any further ###
tar -tpvf /mnt/fat/ubackup.tar  # test the archive to be sure
cd /
umount /mnt/ubuntu
mkfs.reiserfs /dev/hda4  # create a reiserfs on /dev/hda4
mount /dev/hda4 /mnt/ubuntu
cd /mnt/ubuntu
tar -xpvf ../fat/ubackup.tar
nano -w etc/fstab
## change the filesystem from ext3 to reiserfs on the relevant entry ##
## <ctl>x to exit ##
```

---

### Post by nanotube on 2006-06-21
[QUOTE=thasheep]bunch of useful stuff[/QUOTE]
thanks! i will give this a shot when i get around to it. :)

---

