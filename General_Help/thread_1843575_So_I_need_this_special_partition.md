---
title: "So I need this special partition"
date: 2011-09-13
forum: General Help
---

### Post by wthelpp on 2011-09-13
So I want to manually partition my ubuntu ...

I want 90gb to be ubuntu
5 gb to be swap 
and the rest to be Fat32 storage media partition.

How do I do it ?

What are the things I have to do ...

Do I have to make a /home folder ???

I am confused ... help.

---

### Post by MG&amp;TL on 2011-09-13
1. Boot cd.

2. select 'install ubuntu'

3. Manually partition. ('something else'). There's some good instructions online.

4. Install. and you're done.

No, you do not need a home folder, if you only want 'ubuntu' not root and home.

You can just allocate ubuntu ~=95GB in the 'install alongside windows' but this won't be terrifically accurate.

---

### Post by coffeecat on 2011-09-13
You might find this link useful:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

The "something else" option in the installer that MG&TL mentions is a good way of doing it, but the link describes the use of Gparted which is what some prefer. You have a choice! :)

By the way, why a FAT32 partition? Do you have Windows and want a shared data partition? If so, NTFS would be a better choice. If you don't have Windows, then a Linux filesystem would be better.

---

### Post by wthelpp on 2011-09-13
> **MG&TL said:**
> 1. Boot cd.

2. select 'install ubuntu'

3. Manually partition. ('something else'). There's some good instructions online.

4. Install. and you're done.

No, you do not need a home folder, if you only want 'ubuntu' not root and home.

You can just allocate ubuntu ~=95GB in the 'install alongside windows' but this won't be terrifically accurate.



Can you link me to a guide ?

and should I create all / , /boot, /home and swap folders separately ?

BTW I don't need the fat32 for windows. I need it for like storage so I can transfer videos and watch it on my ps3.

---

### Post by coffeecat on 2011-09-13
> **wthelpp said:**
> 
BTW I don't need the fat32 for windows. I need it for like storage so I can transfer videos and watch it on my ps3.

Ok understood. Yes, the Ps3 will only recognise FAT32 formatted USB drives. But your internal partition can be anything you want. If you are streaming over the network to the PS3, the PS3 won't know or care about the filesystem on your media partition.

---

### Post by MG&amp;TL on 2011-09-13
[https://help.ubuntu.com/community/WindowsDualBoot#Manual%20partitioning]("https://help.ubuntu.com/community/WindowsDualBoot#Manual%20partitioning")

and

[http://www.basicconfig.com/ubuntu_desktop_manual_partition_guide]("http://www.basicconfig.com/ubuntu_desktop_manual_partition_guide")

---

### Post by wthelpp on 2011-09-13
> **coffeecat said:**
> Ok understood. Yes, the Ps3 will only recognise FAT32 formatted USB drives. But your internal partition can be anything you want. If you are streaming over the network to the PS3, the PS3 won't know or care about the filesystem on your media partition.

Yeah I just want ps3 to recognize it as a storage drive. Nothing else.

Can you provide me with instructions on how I can do this ?

---

### Post by coffeecat on 2011-09-13
> **wthelpp said:**
> Yeah I just want ps3 to recognize it as a storage drive. Nothing else.

Can you provide me with instructions on how I can do this ?

You want to format a USB drive as FAT32? Use Disk Utility.

Or do you mean you want to know how to set up streaming media from your computer to your PS3? That's a whole different question and needs its own thread. Good luck with that!

---

