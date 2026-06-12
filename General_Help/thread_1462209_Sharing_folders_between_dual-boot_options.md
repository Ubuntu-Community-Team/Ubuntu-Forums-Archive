---
title: "Sharing folders between dual-boot options"
date: 2010-04-25
forum: General Help
---

### Post by PyroFX on 2010-04-25
I am still pretty new to ubuntu and only finished installing it last night and am in the process of getting everything set up.

One thing I have noticed and am curious about is that in Ubuntu, I can access the folders that I have created in XP.  What I would like to know is whether or not it is possible to share or link folders between the two OS.

For example, I try to keep my files organized as best I can and had been keeping pictures in my XP "My Pictures" folder, but have to do a bit of directory digging to get to that same folder from Ubuntu.

---

### Post by Gatemaze on 2010-04-25
From what you are describing you have one xp partition for both the OS and your data... Not a very good practice for any OS... Regarding sharing files between the two operating systems you could have the following minimal partitioning:

partition 1: XP
partition 2: ntfs partition for sharing between the two operating systems
partition 3: /
partition 4: swap (if you need)

You can configure the two systems to use partition-2 for all their purposes, under XP you can define where My Documents, My Pictures, etc. point out. Under Linux, there's no as such configuration, you can make a link on nautilus for quick access.

I would also recommend having a separate /home partition, but know that you can only have 4 primary partitions.

---

### Post by Gatemaze on 2010-04-25
Ooops, ignore my previous answer it is a bit more complicated... In order to do what you want just do the following:

1. Open nautilus (file browser)
2. Go to the directory you want
3. Press ctrl+d or click on Bookmars/Add bookmark


If you want create a symlink in your /home directory then this would be:
1. Open a terminal
2. $ cd
3. ln -sf <target> <link-name>

An easier way might be from nautilus, right-click on the folder, Make link, cut+paste the link where you want.

---

### Post by _0R10N on 2010-04-25
If my guess is correct, what you're trying to is keep access to your Windows files from Ubuntu, without needing to surf across several folders.
So, a practical way to accomplish this is by creating a symbolic link to your Windows folder wherever you want it to be.

If you never used the ln command the syntax is
```
ln -s <source_folder> linkname
```
where..
The -s switch indicates that you'll creating a symbolic link, and not a hard one.
The first argument specifies the location of the folder you're trying to link. This has to be the path where Ubuntu mounts your Windows partition, plus the path to the folder.
Let's assume Ubuntu mounts the partition in 
```
/media/windows
```
and your folder is located in
```
C:\\MyFiles\MyPictures
```
The second argument specifies the location where the link will be. Let's assume you want it in
```
/home/user/Pictures
named
MyWinPics
```

The command you should run is
```
ln -s /media/windows/MyFiles/MyPictures /home/user/Pictures/MyWinPics
```

Kind regards!

_0R10N >>

---

### Post by PyroFX on 2010-04-25
Thanks! that did it. Both through nautilus and the terminal work fine (I tried it both ways just to try to get used to it)

The only issue I had was learning how to make the terminal accept a space in my source file.

---

### Post by Gatemaze on 2010-04-25
> **PyroFX said:**
> 
The only issue I had was learning how to make the terminal accept a space in my source file.

You can use double quotes or the \ character.

e.g. "My Documents"
pr My\ Documents (in this case auto-completion still works)

---

