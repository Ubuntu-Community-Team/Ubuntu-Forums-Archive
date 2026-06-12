---
title: "raid problem after reboot"
date: 2010-08-04
forum: General Help
---

### Post by agurkas on 2010-08-04
Hi guys,

I hope someone will help with this.

problem in short:
I cannot figure out why mdadm software raid fails to autodetect and assemble raid1 array members after every reboot. 
Somehow  it assembles raid members wrongly. After I fix it manually it works  fine again until the next reboot. It seemed to work fine initially. 

more details:
on boot mdadm assembly is wrong. what I get is
cat /proc/mdstat:
**md9: active raid1 sdb[COLOR=Red]_1_[/COLOR] sda[COLOR=Red]_0_[/COLOR]**(which absolutely wrong - no idea how it ends up with this).
other members are not listed at all. Ubuntu fails to mount and boot stops with initramfs prompt.
then I have to manually do:
mdadm --stop /dev/md9
mdadm -A --scan
now it assembles all raid volumes correctly.
cat /proc/mdstat:
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
**md9 : active raid1 sda9[0] sdb9[1]**
      7378880 blocks [2/2] [UU]
md0 : active raid1 sda8[0] sdb8[1]
      173521856 blocks [2/2] [UU]
md1 : active raid1 sda7[0] sdb7[1]
      97659008 blocks [2/2] [UU]
md6 : active raid1 sda6[0] sdb6[1]
      9767424 blocks [2/2] [UU]
md2 : active raid1 sda5[0] sdb5[1]
      97659008 blocks [2/2] [UU]
      
then it boots and works fine till next reboot.

I am using 
Ubuntu Lucid lynx with grub2.
Box  is Dell XPS420 with 2 hard drives and fake raid controller. It had fake  raid0 installed by default with windows but I disassembled and disabled  that in BIOS and created Linux software raid basically from scratch  using alternative Ubuntu install.

thanks for help,
agurkas

---

### Post by agurkas on 2010-08-04
solved it myself.
I deleted raid member md9 (was not used anyway)
deleted partitions that were used in that raid.
/dev/sda9
/dev/sdb9
not sure if that makes any difference but I placed raid members in mdadm.conf in order by md number 0,1,2,6
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=41ea4263:2d9ec7d3:21f2bbc1:ca3ddc1f
ARRAY /dev/md1 level=raid1 num-devices=2 UUID=6977edd0:1bc5a44e:5611f15b:a92b01a9
ARRAY /dev/md2 level=raid1 num-devices=2 UUID=c0612d2a:3ce4c7c9:3d186b3c:53958f34
ARRAY /dev/md6 level=raid1 num-devices=2 UUID=7ce4a26e:1ffb7c27:5611f15b:a92b01a9

now it boots with no problem at all.

 From fdisk **I have noticed has sda8 partition end  and sda9 partition start was the same cylinder number 59883 for some  reason. I thought that might be a problem and decided to delete that partition (sdb8/9 as well).**

fdisk -l 
/dev/sda8           38281       59883   173521920   fd  Linux raid autodetect
/dev/sda9           59883       60802     7378944   fd  Linux raid autodetect


regards

agurkas

---

