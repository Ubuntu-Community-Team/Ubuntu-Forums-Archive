---
title: "Recovering Accidentally Destroyed LVM2 Information"
date: 2011-04-26
forum: General Help
---

### Post by cjstreeter on 2011-04-26
Ok, so I'm stupid and made a serious and grave mistake. On my linux box running Ubuntu 10.10, I have a 1.5TB RAID array that I had originally setup using the instructions located [here]("http://www.gagme.com/greg/linux/raid-lvm.php"). The RAID array is a 4 x 500GB RAID 5 array with an ext3 formatted filesystem and is not my boot device. The RAID array was just used for storage. The LVM setup is a single physical volume (the RAID device) and a single logical volume that makes up the entire physical volume.

So here is the list of steps that I ended up doing, based on the contents of the files in [FONT="Courier New"]/etc/lvm/archive[/FONT] (one file was created before each step, and the file lists what the command was):

```

lvremove /dev/raid_vg/lv0
lvcreate -l 357702 raid_vg -n lv0
lvremove raid_vg
lvcreate -l 357702 raid_vg -n lv0
lvremove raid_vg
vgexport raid_vg
vgimport raid_vg
vgscan
lvremove raid_vg
vgcreate raid_vg /dev/md1
```

So, I accidentally called [FONT="Courier New"]lvremove[/FONT] instead of [FONT="Courier New"]lvchange -a n[/FONT] Then I realized my mistake and tried to restore the logical volume. But that made the disk seem empty.

Now, I'm not sure, but I don't think the data was wiped (at least not all of it). I've cloned the device with ddrescue just so I don't loose anything and can experiment on the image.

Now, my question is then, is it possible to restore the LVM information to the disk and get my filesystem back? I've got the configuration files in [FONT="Courier New"]/etc/lvm/archive[/FONT] which give me the start extents, sizes and extent counts.

Any help that anyone might be able to provide would be extremely appreciated. I was an idiot and screwed myself. I just hope that it was temporary and I can get my data back.

---

