---
title: "Is it possible to triple boot with common storage?"
date: 2010-12-03
forum: General Help
---

### Post by rejinarudo on 2010-12-03
Hello guys. I'm just a newbie so I just want to ask if I can able to triple-boot Windows XP, Ubuntu, and Kubuntu, but with a common storage. Is it possible?

My plan is to install all three OS in different partitions but I want to reserve a particular partition in where all of their installed programs will be installed.

Windows--------------|
Ubuntu---------------|----Common Installation path?
Kubuntu--------------|

I will be very pleased with your answers. Thank you! :D

---

### Post by pricetech on 2010-12-03
You'll find that windows programs don't work in Linux and vice versa.

You can have a common data store, but not an application store.

---

### Post by 3Miro on 2010-12-03
The answer is both yes and no. In windows, you can select where you want to install programs, in Linux you usually don't. You can play with that, but it is very hard. Also, there is no reason for those systems to share a common place for installing programs, since Ubuntu, Kubuntu and Windows will all have different programs installed.

Another problem is that while Linux reads all partition formats, windows only reads NTFS and FAT; ot make windows read the Linux ext2/3/4 formats you have to install special windows software.

Here is what you can do:

1. Get three partitions that will contain Ubuntu, Kubuntu and Windows. Use ext4 for Linux and NTFS for windows (you will also need Linux swap and windows boot partition).
2. Get one more ext4 partition that will have wine installs (that is if you are using wine). This can be common between Ubuntu and Kubuntu.
3. Get one NTFS partition where you will keep media and documents that can be shared between all three systems.

I have e similar setup with 5 versions of Linux (no windows, everything is ext4 for me). You can then use symlink to make sure everything is properly accessible. You can symlink things like Documents and Downloads from Ubuntu and Kubuntu to a common folder. Symlink is like a very powerful shortcut, here is how you can create one from the terminal:

```
 ln -s /path/to/common/folder new/folder/for/association
ln -s /media/CommonFiles/Downloads /home/myname/Downloads 
```

---

### Post by WorMzy on 2010-12-03
Yesno.

Yes it's possible, but not quite as you described.

You can't install Linux programs to an NTFS partiton, and likewise, you cannot install Windows programs to ext# partitions*. Also, you shouldn't really use the same root for multiple Linux distributions.**

However, you can use a NTFS storage partition for your personal files (e.g. Videos, Documents, Pictures, etc), and have that available on both Windows and Linux. Doing so is *almost**** risk free, and makes having multiple OS' a lot easier to work with.

*Not entirely true, I believe you *can* install Windows apps to ext2/3, but you're likely to run into problems, particularly with performance). You can probably install Linux apps to NTFS, but you're even more likely to run into problems doing this, since NTFS doesn't support Linux file systems.

**instead, what you can do is install multiple Desktop Environments to *one* partition. In this case, install kubuntu-desktop on a Ubuntu installation, and you'll be able to pick which one you want use when you log in.

***Linux-to-NTFS support has no guarantees.

---

### Post by Leftside on 2010-12-03
Never mind.

---

### Post by rejinarudo on 2010-12-03
Thanks for the info 3Miro. :D

Gotta try this later. Haha!

---

