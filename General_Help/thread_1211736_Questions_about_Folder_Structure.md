---
title: "Questions about Folder Structure"
date: 2009-07-13
forum: General Help
---

### Post by stvdel on 2009-07-13
Hello, I am still really new to Ubuntu. One of the things that I still have never really figured out is what the different folders are for and what should be put where. If there is any good links explaining this please let me know. 
Some of the problems I have for example
1. Where is the best place to save personal files
2. When downloading new programs where should I download them to? The desktop? After I extract them where should I save them to?

---

### Post by shinnphoto on 2009-07-13
Hi, stvdel, 

Welcome to Linux!  Your first question is really simple to answer.  The second is more in-depth.  

1. Save all your files in your /home directory.  You should have a directory called /home/{YOURUSERNAME}.  Use that for your files.  

2. Here's a great audio podcast on the Linux directory structure: [http://www.linuxreality.com/archives.php#11](http://www.linuxreality.com/archives.php#11).  The entire series of 100 shows is worth listening to, but this episode should answer a few of your questions about the filesystem.

Enjoy, 
Andrew

---

### Post by mthalis on 2009-07-13
Read this it gives you some idea.
[http://www.ubuntugeek.com/linux-or-ubuntu-directory-structure.html](http://www.ubuntugeek.com/linux-or-ubuntu-directory-structure.html)

---

### Post by vinutux on 2009-07-13
> **stvdel said:**
> Hello, I am still really new to Ubuntu. One of the things that I still have never really figured out is what the different folders are for and what should be put where. If there is any good links explaining this please let me know. 
Some of the problems I have for example
1. Where is the best place to save personal files
2. When downloading new programs where should I download them to? The desktop? After I extract them where should I save them to?


...............

1. Home folder is your MyDocuments in ubuntu ..so saved there everything

Places-->Home folder

2. put everything including programs music videos in home folder


/ is single folder cotain everything in ubuntu there is not seperate Parition system existed like C D E 

just googling "Linux file system" for more info

---

### Post by decoherence on 2009-07-13
Good answers and links above. I'll just write a short summary.

All folders (or directories as they are more commonly called in the unix world, but it doesn't matter) live under the root folder, which is referred to as "/" on the command line, "File System" in the latest version of the Ubuntu desktop and "Root" in Kubuntu's desktop. "/" is the most common and longest standing way of referring to the root directory, though, regardless of if you're talking about desktop or command line.

Under that are various directories (usr, lib, etc, var and others) that store system information. You generally don't have to care about what is in them.

Another folder under / is "home" and under home is a folder named after your username. This is called your home folder (or directory.)

Ubuntu sets up some default folders in your home folder for things like pictures, documents, music and so on, but all of these are just suggestions. You can organize your home folder however you like. If you like to download new programs to your desktop, then go ahead (btw, you know about the package manager, right? that's how you're supposed to get most programs.)

Anyway, as a general rule, you should put everything in your home folder unless you have some reason to do otherwise. Where you put things in your home folder doesn't really matter... at worst you might have to open the preferences of a program to tell it about a new location, for instance telling your photo management program to use /home/stvdel/Photos rather than /home/stvdel/Pictures.

Also, while "/" is short form for saying "the root folder," "~/" is short for saying "your home folder." There are a few of these non-obvious conventions, but not too many and they're generally pretty useful.

---

### Post by Andy06 on 2009-07-13
I for one think that it is a good idea to completely bypass the folder structure of ALL OSes for your personal files.

I always have a separate partition with these folders:
Documents
Music
Pictures
Videos
Downloads/Other

Having a separate NTFS partition means I can read those files from any OS (you are stuck with reading files from your home folder only from linux) and I hate Windows pulling in my personal files into various programs that auto scan certain directories (such as music and pictures).

Most important reason though it you can freely install and uninstall OSes without touching your personal files if they are on a separate partition. Trust me, on Linux, you will be doing fresh installs a lot :D

IMO this is the only way to go if you dual boot or do a fresh install every new release, its much better than having a separate /home partition which tends to break settings sometimes.

---

### Post by renbla on 2009-07-13
Yeah, the best place is your /home/username folder, it's the only directory that give you the full permission by default to do any thing: read write, execute. So you don't have to worry about losing any part of you data. Beside, the home folder already contain Music, Document, Picture.... so fell free to fill them up ;)

---

### Post by stvdel on 2009-07-14
Thanks everyone! I will start studying these things right away.

---

### Post by CatKiller on 2009-07-14
> **stvdel said:**
> One of the things that I still have never really figured out is what the different folders are for

[This]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard") is probably a good place to start.

---

### Post by vinutux on 2009-07-14
> **stvdel said:**
> Thanks everyone! I will start studying these things right away.


ok plz mark thead SOLVED

---

