---
title: "ext3 partition recognized incorrectly as silicon_medley_raid_member"
date: 2011-03-21
forum: General Help
---

### Post by rmemm on 2011-03-21
I have a very strange issue.  I have a desktop Ubuntu 10.04 system that has worked just fine for months.  Now suddenly grub won't find the root partition which is an ext3 partition (/dev/sda2).

The strange thing about this -- I can boot with the install CD and can mount it just fine when using mount -t ext3.  If I don't supply the "ext3" type however it identifies the type as "silicon_medley_raid_member" and can't mount it.  If I go into the Ubuntu 10.04 Admin>Disk Utilty -- it too identifies the type of the partition as "silicon_medley_raid_member" not ext3.  Same with blkid -p.  With that I get:

/dev/sda2: VERSION="42758.8269" TYPE="silicon_medley_raid_member" USAGE="raid" 

I have other ext3 partitions that are recognized OK.  When I mount the strange partition forcing ext3 -- it too seems ok.  I ran fsck.ext3 on it -- with -f - and no errors were found.  I backed up the partition with tar -- again -- no errors archiving.   I've even tried zeroing the first 1024 bytes of the partition -- that had no effect on this issue.

So what is going on with this.  Any ideas? Any ideas how to fix this issue?  What am I missing?

Any thoughts would be appreciated.

Thanks.
Rob

---

### Post by rmemm on 2011-03-22
An update.  It seems that it has something to do with the partition itself.  I copied /dev/sda2 to /dev/sda1 using dd -- and the problem went with the copy.

The strange thing about this is that there are no bad blocks, and e2fsck does not find any issues (even with the -f and -cck options).

So now I'm working on just zeroing sda1 with dd, and then reformatting to ext3 manually, and doing a file level copy into the pristine partition to see if this fixes the problem.

What bothers me about this is that either (a) e2fsck and fsck.ext3 is missing something, (b) the partition is valid by there's something wrong with the autorecognition process used by grub, Disk Tool, and blkid routines.  Even if starting with a pristine format fixes the problem -- it seems like there's no guarantee that this just doesn't magically come back.

Any thoughts.

Rob

---

### Post by Magma828 on 2011-04-18
I'm having the exact same problem, with my ext3 partition being recognised as 'silicon_medley_raid_member'.

If I try to mount it using this:
```

sudo mount -t ext3 /dev/sda5 /mnt/target

```
I just get the following error:
> 
mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


and when I type dmesg, I get this:
> 
ubuntu@ubuntu:~$ dmesg | tail
[  707.336562] EXT3-fs: sda5: couldn't mount because of unsupported optional features (240).


Does anyone know how to mount the partition so I can access the files?

---

### Post by oldfred on 2011-04-18
If you are sure you do not have RAID, you can try this. Were the drives ever in a RAID set. Drives retain meta data. If you do not have dmraid you may have to install it, but then can uninstall it.

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discusion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

---

### Post by rmemm on 2011-04-18
For what it's worth -- I gave up on solving my problem regarding the silicon_medley_raid_member, and just reinstalled my OS.  For me I always keep the OS and home partitions separate so it was easy.  And to make sure nothing was there - I zeroed the partitions with dd before reninstalling -- and I chose ext4 after the reinstall -- with the hope the problem would not return again.  So I never resolved my issue except by brute force.

I am surprised that you could not mount the partitions -- because I never had a problem with this.  I ran e2fsck on my ext3 partition though, then mounted it manually and backed it up before reinstalling.  No problem in my case.  The thing that was strange in my case -- auto recognition always through it was a raid member -- but if I manually specified a type of ext3 on the mount command it worked great.  Strange.

Other thing I found out in the process is that Puppy linux worked really well in mounting my partitions -- much better than the Ubuntu CD.  Puppy did NOT have the autorecognition problem and always knew it was not a raid member.  If you need a rescue CD -- maybe try puppy linux -- worked great form me.  It's very small and fast -- and runs all in memory an can be put on USB sticks and CDs.

Take care,
Rob

---

### Post by Magma828 on 2011-04-19
I managed to mount the partition by forcing it to use ext4 (rather than ext3, which it is). It's still being recognised as that raid thing though, so wont boot. I think I'll have to do the same as you and reinstall, it's just a lot of trouble to copy over all my files and reinstall all the programs.

---

### Post by effell on 2012-02-03
Same thing just happened to me as to the OP, also using 10.10 Maverick. I managed to boot it using the grub console, at the expense of quite a few hours. Since support for Maverick will expire this April, I will probably take the opportunity to upgrade. Still, it would be a good idea to track this particularly nasty bug down. In case it helps: 64 bit version, using an Intel SSD on a Thinkpad, had just installed dropbox, no recent kernel changes.

---

