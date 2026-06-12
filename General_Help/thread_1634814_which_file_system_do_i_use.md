---
title: "which file system do i use?"
date: 2010-12-01
forum: General Help
---

### Post by TheOne...more on 2010-12-01
hi i just bought this hdd [http://www.samsung.com/global/business/hdd/productmodel.do?group=72&type=94&subtype=98&model_cd=248](http://www.samsung.com/global/business/hdd/productmodel.do?group=72&type=94&subtype=98&model_cd=248) and i don't know which fs to use.

i'm already using xfs because it's dynamic but i read that jfs and reiser fs are dynamic too, so which one do i use whether for storage or os.

thanx

---

### Post by Sef on 2010-12-01
I would just use ext4, unless there is some reason that you need a dynamic file system. Is there?

---

### Post by TheOne...more on 2010-12-01
i guess if i used some of the space of the disk for operating system, that would suggest the need for a dynamic fs.

maybe what i want to do is a little bit vague, so here it is. i want to keep the entire disk as one partition for whatever use.

so what do you think?

i'm just trying to get opinions, you know a couple of heads is always better than one.

---

### Post by runeh76 on 2010-12-01
> **Sef said:**
> I would just use ext4, unless there is some reason that you need a dynamic file system. Is there?


I tryed ext4 but i didnt get ubuntu work. It works only with ext3.

---

### Post by a-user on 2010-12-01
what ubuntu version are you using? ext4 i working at least since 9.10 without problems.
i am using ext4 too. alternatively i would use xfs. this two are currently the best two for most situations.

---

### Post by WorMzy on 2010-12-01
I just use ext4, but here's a quote with some info on the main filesystems:

[QUOTE=https://wiki.archlinux.org/index.php/Beginners%27_Guide#Filesystem_Types]1. ext2 Second Extended Filesystem- Old, reliable GNU/Linux filesystem. Very stable, but without journaling support. May be inconvenient for root (/) and /home, due to very long fsck's. An ext2 filesystem can easily be converted to ext3. Generally regarded as a good choice for /boot/.

2. ext3 Third Extended Filesystem- Essentially the ext2 system, but with journaling support. ext3 is backward compatible with ext2. Extremely stable, mature, and by far the most widely used, supported and developed GNU/Linux FS.

High Performance Filesystems:

3. ext4 Fourth Extended Filesystem- Backward compatible with ext2 and ext3. Introduces support for volumes with sizes up to 1 exabyte and files with sizes up to 16 terabytes. Increases the 32,000 subdirectory limit in ext3 to 64,000. Offers online defragmentation ability.

4. ReiserFS (V3)- Hans Reiser's high-performance journaling FS uses a very interesting method of data throughput based on an unconventional and creative algorithm. ReiserFS is touted as very fast, especially when dealing with many small files. ReiserFS is fast at formatting, yet comparatively slow at mounting. Quite mature and stable. ReiserFS is not actively developed at this time (Reiser4 is the new Reiser filesystem). Generally regarded as a good choice for /var/.

5. JFS - IBM's Journaled FileSystem- The first filesystem to offer journaling. JFS had many years of use in the IBM AIX® OS before being ported to GNU/Linux. JFS currently uses the least CPU resources of any GNU/Linux filesystem. Very fast at formatting, mounting and fsck's, and very good all-around performance, especially in conjunction with the deadline I/O scheduler. (See JFS.) Not as widely supported as ext or ReiserFS, but very mature and stable.

6. XFS - Another early journaling filesystem originally developed by Silicon Graphics for the IRIX OS and ported to GNU/Linux. XFS offers very fast throughput on large files and large filesystems. Very fast at formatting and mounting. Generally benchmarked as slower with many small files, in comparison to other filesystems. XFS is very mature and offers online defragmentation ability. [/QUOTE]

Feel free to experiment.

---

### Post by runeh76 on 2010-12-01
> **a-user said:**
> what ubuntu version are you using? ext4 i working at least since 9.10 without problems.
i am using ext4 too. alternatively i would use xfs. this two are currently the best two for most situations.

I have 10.10 but i think that problem was my hd..dunno sure. But install just didnt work with ext4. Switching ext3 and it worked. I have used linux since redhat.

---

### Post by TheOne...more on 2010-12-01
thank you guys for all the perspective you brought in, i was afraid that you wouldn't have noticed that there is some depth in the question.

and i didn't reallize how much jargon did drop out of my brain since i last time fixed a fs...a year or so! until you began replying. i think i need a good reread.

also i thought that ext4 having some drawbacks more than xfs or jfs it still might be under development, i remember that i have read that it was officially released but there were articles about it that made me hezitate/give it more time...until it matures.

actually i was going to choose jfs for xfs, but it seems that i read that xfs can be used as grub root while jfs couldn't. but after i installed xfs i found that it wasn't too. that's why i didn't use jfs.

actually in the cutting edge area both jfs and xfs are pretty competitive it was hard for me to choose which to use, the main reason for me to start the post.

but what i really like about both is how the partition is divided into chunks so that if an area is corrupt not all of the data is lost, the journal is cutting edge but power loss isn't an alltime issue, it just happens when temperature differences are big.

---

### Post by a-user on 2010-12-01
the recently benchmarks on phoronix between xfs, ext4, brtfs and the one beginning with "z" ( :P forgot the name), demonstrated that in most cases ext4 and xfs are currently the best performers.

if i rember right, jfs has stopeed forther developing and reiser has several other problems.

so best choices currently seem to be ext4 and xfs.

---

### Post by TheOne...more on 2010-12-01
that's interesting, i seriously need a good reread!!!:-k

---

### Post by akand074 on 2010-12-01
Yeah use ext4, there should definitely not be any issues since 9.10. I tried a lot of different file systems. I ended up back with ext4. It's still benchmarked highest overall. Though other FS are better for particular tasks but not by all that much. Btrfs seems to have a good future, but right now its not that good yet. I hear Ubuntu is planning on adopting it as the main FS in the future. I'm not sure of its validity though.

---

### Post by a-user on 2010-12-01
regarding brtfs, i was very disapointed after i read so much hype about it. at least at current state is quite sucks in most cases. but there are some scenarios it shines. for most user this not the matter.

i would say that xfs is slightly the better performer, but i still woudl prefer ext4 in most cases cause you can use it everywhere, even on windows there are good reading tools for it. it is more portable. well it depends on your intension.

---

### Post by TheOne...more on 2010-12-01
it actually is a bit dissapointing knowing that jfs isn't that competitive anymore, i thought it was going to drop out much later because it's backed by a big company.

---

