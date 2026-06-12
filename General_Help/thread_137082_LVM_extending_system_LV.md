---
title: "LVM: extending system LV"
date: 2006-02-27
forum: General Help
---

### Post by zagor on 2006-02-27
Hi,

/usr on my Breezy is full.
It's mounted on a Logical Volume.
I've extended the Logical Volume following [http://www.tldp.org/HOWTO/LVM-HOWTO/extendlv.html](http://www.tldp.org/HOWTO/LVM-HOWTO/extendlv.html).
but I can't resize it, for I can't umount it!!!

In detail:
I have 3 PV: hdb7, hdb11, hda10
hdb7 and hdb11 are in the group vg_ubuntu.
hdb7 is fully used by lv_data (where I've mounted /usr, ext3)
hdb11 is fully used by lv_system (where I've mounted /, reiserfs)
hda10 was inside another VG, which I've used with RedHat (ext3).

Therefore, I've sudo-ed:
vgremove VolGroup00
vgextend vg_ubuntu /dev/hda10
lvextend -L1G /dev/vg_ubuntu/lv_data

at this point, the HowTo says I need to resize, but I can't umount /usr.

Ubuntu live says there's a superblock and can't resize.
Auditor live can't even see the LVs.

ext2online is not available on my system and I couldn't find it with synaptic.

Suggestions?

Thanks

---

### Post by piedamaro on 2006-02-27
Ciao,
you can't unmount /usr while you have the system up and running, boot in recovery mode (single user, init=/bin/bash or whatever), and do all your lvm configuration from there.

---

### Post by yanik on 2006-02-27
or use a livecd/rescuecd

---

### Post by zagor on 2006-02-28
Thanks for the suggestions.
No results, though.

After booting in recovery mode, I could umont the /usr partition and run the resize2fs utility.
I've got the same message that I've recieved when booting with the Ubuntu liveCD:

Bad Magic number in super-block while trying to open /dev/vg_ubuntu/lv_data
Couldn't find valid filesystem superblock

Any more suggestions?

Thanks.

---

### Post by evilgold on 2006-03-02
Hi,

lvmextend (and lvmreduce) need filesizes specifed in block size. dumpe2fs should give you information on what block size your filesystem is using. Ext2/3 usally sets at 4k (4096kb) but you should probably double check.

so somthing like
lvextend ######### /dev/vg_ubuntu/lv_data
(# = total blocks for the lvm to fill)
And resize2fs

Read the howto over again before you do it, cause i dont remember exacty.

ohh and to figure out the block size, pull up your calculator and do #ofbytes/4096?

if you want to extend it to 100gbs you would do 100,000,000,000/4096 and use the # that gives you to lvextend.

Again, double check all of this because its been a while since i've done it.

---

