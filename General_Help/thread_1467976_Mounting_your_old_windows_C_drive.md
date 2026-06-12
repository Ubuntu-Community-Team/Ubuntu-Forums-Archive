---
title: "Mounting your old windows C: drive"
date: 2010-05-01
forum: General Help
---

### Post by ShimaNoShinobi on 2010-05-01
So here's the problem

Back in the days my friend installed ubuntu 8.04 on my computer. My hard drive had three partions: "Movies", "Pictures" and the simple "C:". Ubuntu was installed on my "C:" partion. I have since upgraded my ubuntu to 9.04. A while ago i got a new laptop and have decided to install 10.04 on it.

I was planning to simply install ubuntu on the "C:" drive on my laptop but then i noticed that I cannot mount a volume called "19.6 GB media" on my old computer. I presume that this is the "C:" partion on my old windows. I can mount both other volumes though. 

So is it simply so that if I install Ubuntu on C: drive I cannot mount it using ubuntu? This troubles me since I was planning to simply access all my files through this volume. Am I forced to create new partions for my movies and other files in order to access them through Ubuntu. This would be a probem since windows 7 only allows me to free like 29 GB of space from my C: drive and partioning tool I've found online have been pretty expensive.

Any help please?

---

### Post by fyo on 2010-05-01
"C: drive" is not really a good way of describing a partition. In this case, the partition you are referring to may or may not be what Windows would call "C:" (which would typically be the Windows boot partition).

Try starting "Disk Utility" (Palimpsest) or "Partition Editor" (GParted), found in the Administration section of the System menu.

This should give you some information about the partition in question. Post it and we'll take it from there.

---

### Post by ShimaNoShinobi on 2010-05-01
Okay this is what I got from the partion I believe is the one in question:


----------------------------------------------------------------
/dev/sda1
18.00 GiB

File system: NTFS
Size: 18.00 GiB
Flags: boot

Path: /dev/sda1
Mount: Not mounted
Label:
UUID: 82888BD5888BC65F

First Sector: 63
Last Sector: 37752749
Total Sectors: 37752687

Warning:
Unable to read the contents of this file system! bacause of this some operations may be unavailable.
----------------------------------------------------------------

I also want to know how do I prevent this from happening if I install 10.04 on my laptop.

---

### Post by dino99 on 2010-05-01
install MountManager and tweak it as you need (select device in left pane)

---

### Post by ShimaNoShinobi on 2010-05-01
Well... now I managed to mount the volume through Gparted :D I wonder why I couldn't mount it from Places.

Now if I can just get some installing advice I think I'll be fine.

On my new laptop, I have freed space from the default hard drive. Is it okay for me just to install ubuntu on that freed space or should I create a new partion for it? Should I be able to access all my files on the default windows partion from ubuntu like that?

---

### Post by fyo on 2010-05-01
> **ShimaNoShinobi said:**
> On my new laptop, I have freed space from the default hard drive. Is it okay for me just to install ubuntu on that freed space or should I create a new partion for it? Should I be able to access all my files on the default windows partion from ubuntu like that?

Ubuntu really needs its own partition for a proper install.

Since you've already freed space on your drive, you can just install Ubuntu from the CD/DVD. If you don't have a burner (or an optical drive on your laptop), you can install from a thumb/flash drive.

The installer will ask you if you want to delete your entire drive or if you want to create a new partition for Ubuntu (your Windows partition will be resized). Choose the latter ;)

You should have no problems accessing your Windows files from Ubuntu. The problem is the other way around -- your Ubuntu files will not be accessible from Windows. So any files you need to access from Windows should be saved to your Windows partition (or another NTFS/FAT formatted partition).

Remember: Always backup your data.

---

