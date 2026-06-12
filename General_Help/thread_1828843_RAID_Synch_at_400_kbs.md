---
title: "RAID Synch at 400 kb/s"
date: 2011-08-19
forum: General Help
---

### Post by tylersontag on 2011-08-19
Alright, i just had a RAID crash on me (long story, it involved zeroed superblocks and bad recovery's resynching trash data) and i finally gave up reconstructing it and just decided to start over.

I zeroed out all three drives (this was/is a RAID5 with 3 drives) and removed the partition off of them. Using Disk Utility i then created a new LV from the three drives. It comes up degraded and begins to resynch... everything normal right?

then i notice how long its taking, i do a cat /proc/mdstat and this is what i'm staring at


```
recovery =  1.3% (27151372/1953511424) finish=81327.2min speed=394K/sec
```

Rediculous. My RAID card is a RocketRAID 1740, there is no reason for 0.4 MB/s synch speeds. Something has to be wrong here. Any ideas?

---

### Post by YesWeCan on 2011-08-19
This is a fakeraid card, right?

More detail about how you set the drives up would help.

---

### Post by YesWeCan on 2011-08-19
More info here: [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

There are different types of RAID:
1) Windows software RAID, also called fakeraid or host raid or dmraid. Windows requires mobo hardware support and add-on drives.
2) Linux software RAID, also called mdraid or mdadm. This requires no mobo RAID support and is generally considered better than fakeraid, at least around here.
3) Hardware RAID. This is the sort of RAID where the OS doesn't even know there is a RAID array - it just sees a storage device. They are quite expensive: [http://www.adaptec.com/en-us/_common/series6e/?hpBan=6E-US&utm_source=hp&utm_medium=banner&utm_campaign=6E-US](http://www.adaptec.com/en-us/_common/series6e/?hpBan=6E-US&utm_source=hp&utm_medium=banner&utm_campaign=6E-US)

Things will not work properly if you use the wrong Ubuntu drivers. I'd recommend you zero out any dmraid and mdadm super-blocks and start again. If you want to use the card in Windows raid mode, use the dmraid driver. If you want to use linux raid then disable raid in the card and use the mdadm driver.

---

### Post by tylersontag on 2011-08-19
it is managed using the Linux software raid (MDADM)   So should i try zeroing out the superblocks again?  I already have built it twice after zeroing out each of the 3 drives... does mdadm --zero-superblock /dev/md0 do anything?

---

### Post by YesWeCan on 2011-08-20
There are two types of superblock, those created by mdadm and those created by dmraid. I don't know exactly wht you are trying to do or what you set-up is, so I'm just trying to make you aware of a possible problem.

If you run
sudo dmraid -s
It will list any disks that are members of dmraid (have dmriad superblocks)
To delete the blocks on drive sda
sudo dmraid -Er /dev/sda

If you want to assemble the drives as an mdadm RAID, I suppose you need to configure the RAID card to not do any RAID itself and just present the 3 drives as independent drives. Then you can do your mdadm stuff and hopefully it will be fast.

---

### Post by tylersontag on 2011-08-21
I had been and still am managing the LV with mdadm.  I don't have dmraid.  I thought about playing around with the BIOS level menu that comes up on the RAID when i reboot, but i've never had to mess with anything in there before.

Prior to losing all my data on this RAID, it ran fine with MDADM... i don't know the exact speed at which it would do a resynch but it was much faster than 400kbs.

I'm wondering if physically reordering the drives might help to break any existing associations.

---

### Post by tylersontag on 2011-08-25
SO i tried zeroing the blocks again reordering the drives, and building another LV with MDADM.  RAID is still slow.  I tried booting  into the raid BIOS to see if there was any settings i could change, but no dice.    There has to be some setup configuration i'm not doing right, i just can't figure out what..

Could really use some new leads at this point.  I'm out of ideas.

---

