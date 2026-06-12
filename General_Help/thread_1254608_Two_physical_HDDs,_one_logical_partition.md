---
title: "Two physical HDDs, one logical partition"
date: 2009-08-31
forum: General Help
---

### Post by bfrosty on 2009-08-31
Hi experts,

I was wondering how I can get 2TB+ on one logical partition? i.e. contiguous storage.

I'm accepting of the fact that my current server, which runs on desktop architecture, probably doesn't support this. What are my options here?

Thanks! :KS

---

### Post by thinkdez on 2009-08-31
This is possible.  I am going to make some assumptions though.

- You have two, 1TB drives or two drives totaling 2TB.
- You have a separate disk with the OS already installed.

I did this using LVM [Logical Volume Manager.  You could also do this with Software RAID.

LVM

1. First make sure the drives are seen by the system
2. Select the physical drives to be used: sudo pvcreate /dev/sdb1 /dev/sdc1
3. Create a volume group: sudo vgcreate -s 32M vol_grp001 /dev/sdb1 /dev/sdc1
4. Now create the Logical Volume: lvcreate -l 65534 -n my_logical_vol vol_grp001

Now you have a logical volume called /dev/vol_grp001/my_logical_vol.  Format it and mount it and your all set.

Notes:
- Step 2: the -s 32M specifies the size of the extents.  32M is approximately what you need for a 2TB LVM.  You may need to increase it if you plan on expanding the LVM later.
- Step 3: -l 65534 specifies the number of extents to use.  As you want a 2TB drive I specified to use them all, however if you change the size of the extent the max number of extents will be smaller.

You can learn more about LVM's here: [http://linuxhelp.blogspot.com/2005/04/creating-lvm-in-linux.html]("http://linuxhelp.blogspot.com/2005/04/creating-lvm-in-linux.html")

I didn't go into detail on how it works but those are the basic steps.  I recommend that you look into it further so to better understand them.

Hope that helps.

Oh you need the LVM2 packages installed to do this by the way.

---

