---
title: "Is my Ububtu 10.4.2 LTS LiveCD using my hard drive for a swap file?"
date: 2011-06-22
forum: General Help
---

### Post by serj45 on 2011-06-22
I am concerned about the LiveCD touching my HDD at all. Is this a factor, such as using HDD space for a swap file? I thought the whole thing ran off my RAM.

Anyway here's my specs:

MacBook Pro 500GB:
HFS+ Partition w/Snow Leaopard ~400GB
NTFS Parition with WIndows 7 ~100GB
EFI Partition ~200MB

1) Does this mean I have a "swap file" on there I don't know about? I assume both WIndows and OSX use virtual memory to manage RAM when running in their respective operating systems but does that mean Ubuntu LiveCD will use one of my winows or OSX partition's "swap file"? 

2) Or is there an invisiable partition created for LiveCD to use on some unallocated space on my HDD (I don't think there's any but idunno)? 

3) How can I be sure the LiveCD is not writing ANY data to the HDD? I don't believe I have ever explicitly created a swap file in either OSX or windows. 

Thanks!

---

### Post by dFlyer on 2011-06-22
If your running the live cd your not saving anything to your hd. The live cd runs totally in RAM.

---

### Post by slooksterpsv on 2011-06-22
> **serj45 said:**
> I am concerned about the LiveCD touching my HDD at all. Is this a factor, such as using HDD space for a swap file? I thought the whole thing ran off my RAM.
...

1) Does this mean I have a "swap file" on there I don't know about? I assume both WIndows and OSX use virtual memory to manage RAM when running in their respective operating systems but does that mean Ubuntu LiveCD will use one of my winows or OSX partition's "swap file"? 

2) Or is there an invisiable partition created for LiveCD to use on some unallocated space on my HDD (I don't think there's any but idunno)? 

3) How can I be sure the LiveCD is not writing ANY data to the HDD? I don't believe I have ever explicitly created a swap file in either OSX or windows. 

Thanks!

1) Nope it creates a virtual swap file using your RAM. It doesn't touch the HDD at all unless you tell it to mount the HDD or to install.

2) Invisible partition basically. It segments your RAM so the squashfs is mounted and then anything you save gets like 500MB of storage, which is just RAM, meanwhile the other RAM is used for loaded programs, etc.

3) If you don't mount a drive or click on any of your drives in the live cd it won't touch it. The only thing it will do is read the controller to see if a drive is connected and see if it is able to mount any of the drives if you wanted to. None of your data is being touched if you don't tell it to open your hard drive. (Meaning you open the file manager and click on the drive in the left hand side, if you do that it will access your hard drive)

---

### Post by Elfy on 2011-06-22
> 1) Does this mean I have a "swap file" on there I don't know about? I assume both WIndows and OSX use virtual memory to manage RAM when running in their respective operating systems but does that mean Ubuntu LiveCD will use one of my winows or OSX partition's "swap file"? Once you've installed a linux and it creates a swap partition livecd's that I've used will use that when available.

---

### Post by serj45 on 2011-06-22
Thank you all for the prompt answers!

---

### Post by mastablasta on 2011-06-22
you can unplug your hdd and boot only with CD unit :-)

---

