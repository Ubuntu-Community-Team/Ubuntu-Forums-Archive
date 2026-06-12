---
title: "Help with safe Logical Volume reduction"
date: 2012-05-04
forum: General Help
---

### Post by lorewap3 on 2012-05-04
When installing Ubuntu, I had 5 hard drives I set up in a RAID 1 using mdadm to give me 5.4 T. I now have a 6th drive that I want to add to that mix. I want to reduce this by 1TB (which will free up 2 1TB hard drives), raid them to my new 2TB hard drive, and add them back to the LV which will give me a total of 6.4 T. 

How can I safely do this? I'm currently only using 2.6 TB which gives me over 50% of free space. So I know I have the space to do it, but I want to be sure there's no data loss. I know I need to use pvmove and pvreduce, but I'm not sure how to use pvmove as I don't have any 'free extents' according to pvdisplay. Any assistance would be greatly appreciated!

Here are the outputs of display commands. What I want to do is reduce /dev/sol/earth by 1TB, remove /dev/md3 from the sol VG, break up md3 and recreate it using the new hard drive, then re-add it back to the sol VG. I know mdadm, but I'm new to resizing LVM. Any information on how to use extents would be nice. I don't understand how to use extents rather than a size figure, or if it's even necessary. When I try 'lvreduce -L -1T /dev/sol/earth' I get a warning 'THIS MAY DESTROY YOUR DATA'. How can I be sure what it's reducing is only free space and that the space being freed is all on /dev/md3?

Thanks!
Will

**LVDISPLAY:**

  --- Logical volume ---
[B]  LV Name                /dev/sol/earth
  VG Name                sol
  LV UUID                dvWzY5-q1nh-ZYO6-072m-1glL-NAry-rvlwdc
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                5.38 TiB
  Current LE             1411209
  Segments               4
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           251:0[/B]

  --- Logical volume ---
  LV Name                /dev/enterprise/bridge
  VG Name                enterprise
  LV UUID                Mm0Aei-0WoU-EHig-kpwt-K1uk-0pek-sdHuWQ
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                18.62 GiB
  Current LE             4767
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           251:1



**PVDISPLAY:**

  --- Physical volume ---
  PV Name               /dev/md1
  VG Name               sol
  PV Size               894.07 GiB / not usable 1.87 MiB
  Allocatable           yes (but full)
  PE Size               4.00 MiB
  Total PE              228881
  Free PE               0
  Allocated PE          228881
  PV UUID               zF0Phr-o8ue-y8bX-DwUK-HQgT-P1no-nEDAEl

  --- Physical volume ---
  PV Name               /dev/md2
  VG Name               sol
  PV Size               1.78 TiB / not usable 2.87 MiB
  Allocatable           yes (but full)
  PE Size               4.00 MiB
  Total PE              466931
  Free PE               0
  Allocated PE          466931
  PV UUID               d0yROq-MGk8-tQN6-gccD-V9JV-pq3y-u9WW5k

[B]  --- Physical volume ---
  PV Name               /dev/md3
  VG Name               sol
  PV Size               931.51 GiB / not usable 2.87 MiB
  Allocatable           yes (but full)
  PE Size               4.00 MiB
  Total PE              238466
  Free PE               0
  Allocated PE          238466
  PV UUID               pkll7Y-Pmra-SH1C-s9G0-Pct3-4JFy-wfcji1[/B]

  --- Physical volume ---
  PV Name               /dev/md4
  VG Name               sol
  PV Size               1.82 TiB / not usable 2.87 MiB
  Allocatable           yes (but full)
  PE Size               4.00 MiB
  Total PE              476931
  Free PE               0
  Allocated PE          476931
  PV UUID               HMXIlb-OhZ5-Pwom-jJw1-sE5e-Uozr-Yad3rF

  --- Physical volume ---
  PV Name               /dev/md0
  VG Name               enterprise
  PV Size               18.62 GiB / not usable 2.93 MiB
  Allocatable           yes (but full)
  PE Size               4.00 MiB
  Total PE              4767
  Free PE               0
  Allocated PE          4767
  PV UUID               Dwiuvn-DKEe-Fq6n-CN1P-v5rO-jCdU-OprRce

---

