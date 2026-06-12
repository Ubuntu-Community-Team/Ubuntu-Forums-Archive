---
title: "Problems with Wine"
date: 2010-06-23
forum: General Help
---

### Post by Gabe15 on 2010-06-23
Greetings Everyone,
Please pardon my inexperience, I am trying out Ubuntu for the first time because I thought it would be fun and I now I have a Windows application I would like to run. I would say I am a medium-level computer geek on Macs, just enough to figure out clever and useful things but not enough to explore the world beyond (Windows, Liunx, programming in general...) just for fun too much, except for this new Ubuntu experience. I like the idea and it seems like a nice community of people supporting it.

I got Ubuntu (10.04 LTS) working (seemingly) fine on my Macbook with Parallels 4.0, no problems there. I installed Wine (1.1.42) and subsequently tried to install the Windows program I wish to use from a CD. The main issue seems to come from that all of the tutorials online say to select the executable file from the application disk for wine to use. On the disk however, there appear to be many different executable files. I picked one with the word "startup" in it just to see what would happen, and it went thru a bunch of steps as if it was installing the software, however the software never worked, which I kind of expected. So I uninstalled it and looked up some information on trying to use the disks autorun with Wine on Ubuntu, at least from my view so it can figure itself out, but I realize now that I don't really know whats going on or what to do now. I've tried going thru different terminal commands from other tutorial sites, and I'm ok with that, enough to follow directions, but it hasn't gotten me anywhere yet.

I've tried installing it straight from the disk, and also from a copied version to avoid the "read-only" permission from the disk, in case that was causing any issues.

Additionally, just in playing with it more, I've tried to redo the same thing I did before, which at least seemed to partially work, but now when I try to select any executable file for Wine to use, it states that it is indeed not an executable file.

Again, I don't know a lot about this, or really anything, but I have a feeling the issue is complicated by the fact that the program has many individual files which all seem to need to be put together by a computer that knows what its doing or by someone much more familiar with this stuff than I. I think there may also be two different applications on the CD.

I've also tried Wine and Winebottler for OSX to avoid going thru Parallels and Ubuntu, but that has been even more confusing so far, and there doesn't seem to be as much support around for it.

If it helps all at, the software is for accessing and uploading information to a database, and below is a screen shot of all of the files on the CD. 

It's not critical I get this to work, but any help would be appreciated.

---

### Post by sanderd17 on 2010-06-23
The autorun.inf file tells you what you need to execute. But if you can do it without wine (if there's a linux alternative for), please don't use wine. Wine doesn't have all the libraries windows has so if a program really needs a specific library that isn't in wine, the program won't work.

Could you also do something in commandline:

cd to the directory of your cd-rom:
```

cd /media/NAME_OF_CD

```
and there execute
```

ls -al

```
and report the result (you dan copy paste by selecting text en middle-clicking where it need to come)

This command is to see the permission of all files.

---

### Post by 73ckn797 on 2010-06-23
If you get the executable file error message when trying to run an exe file from Nautilus, you will have to install through the Wine program and not from Nautilus. I assume that may be how you are trying to do it. If it seems to install but not run, then there are probably libraries/dependencies missing. I have many programs that will install but not work at all in WINE.

---

