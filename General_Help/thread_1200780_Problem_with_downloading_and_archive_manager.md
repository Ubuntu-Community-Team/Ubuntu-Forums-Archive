---
title: "Problem with downloading and archive manager"
date: 2009-06-30
forum: General Help
---

### Post by Liberty or Death on 2009-06-30
Hi, I just downloaded Ubunutu on my laptop through Wubi , I also have Vista on my computer. I think I may have made a mistake with default settings, most things that I try to download, Ubunutu/ Linux keeps sending to "archive manager" and I can't download it, keeps sending me in circles, however some downloads it classifies as a "file package", and they download just fine, a co-worker who is a Linux user said that I could just enter in a code to download, but I'm not used to that and I just want this "archive manager" problem done away with, it would be simpler. Can you help? ](*,)

---

### Post by mcduck on 2009-06-30
Simple, when you click for some file to download use the "Save File" option, not the "Open With"-option.

Or right-click the link and select "Save Link As..".

(Something makes me think that you are trying to download programs, if that's the case you should know that downloading software from web pages and installing manually isn't the way things are usually done in Linux, we have far better ways to manage software than that. Read this: [Installing software in Ubuntu]("http://www.psychocats.net/ubuntu/installingsoftware"))

---

### Post by Liberty or Death on 2009-06-30
> **mcduck said:**
> Simple, when you click for some file to download use the "Save File" option, not the "Open With"-option.

Or right-click the link and select "Save Link As..".

(Something makes me think that you are trying to download programs, if that's the case you should know that downloading software from web pages and installing manually isn't the way things are usually done in Linux, we have far better ways to manage software than that. Read this: [Installing software in Ubuntu]("http://www.psychocats.net/ubuntu/installingsoftware"))
I tired to save file, but when I went to open it, same problem... I could try the "save link as". Thanks for the link, I'm probably too used to XP and Vista's ways of downloading.

---

### Post by mcduck on 2009-06-30
> **Liberty or Death said:**
> I tired to save file, but when I went to open it, same problem... I could try the "save link as". Thanks for the link, I'm probably too used to XP and Vista's ways of downloading.

Only makes sense that what you downloaded opened in archive manager if you indeed were trying to download programs. Programs distributed on web pages are not usually in executable installers, or even any other compiled format. Usually they are simple .tar.gz archives (similar to .zip or .rar) that contain the source code for the program.

In other words, what you downloaded was just an archive file, so it opened in archive manager when you clicked it. ;)

Better stick with Ubuntu's own package management tools, they'll download, configure and install programs for you, and also handle automatic updates and, in case you need to, removing of software for you without you ever having to open the web browser. :D

And with tens of thousands of packages available this way there's rarely any reason to actually download anything yourself. But if you can't find something from the package manager and really have to download it from the net, try to look for .deb packages made for Ubuntu. These can be installed simply with a double click. The tar.gz packages that contain source code are the last option you'd usually only use if something simply isn't available in any binary format.

---

### Post by Liberty or Death on 2009-06-30
> **mcduck said:**
> Only makes sense that what you downloaded opened in archive manager if you indeed were trying to download programs. Programs distributed on web pages are not usually in executable installers, or even any other compiled format. Usually they are simple .tar.gz archives (similar to .zip or .rar) that contain the source code for the program.

In other words, what you downloaded was just an archive file, so it opened in archive manager when you clicked it. ;)

Better stick with Ubuntu's own package management tools, they'll download, configure and install programs for you, and also handle automatic updates and, in case you need to, removing of software for you without you ever having to open the web browser. :D

And with tens of thousands of packages available this way there's rarely any reason to actually download anything yourself. But if you can't find something from the package manager and really have to download it from the net, try to look for .deb packages made for Ubuntu. These can be installed simply with a double click. The tar.gz packages that contain source code are the last option you'd usually only use if something simply isn't available in any binary format.
OK, I'll stick with package management tools from now on. So these downloads that I were trying to get were not actually made for Linux Ubunutu, and so they would not open properly?

---

### Post by oldos2er on 2009-06-30
Source code can be compiled on any Linux system. It's much easier for a newbie (and an oldbie too) to let the package manager handle installation, removal, and updates of software.

---

### Post by mcduck on 2009-06-30
> **Liberty or Death said:**
> OK, I'll stick with package management tools from now on. So these downloads were not actually made for Linux Ubunutu, and so they would not open properly?

No, they were made for Linux, but not specifically for Ubuntu, they are in the most basic format a program can be (the original source code the programmer wrote when making the program) and can be compiled into a working program that runs on any Linux version.

It's just that compiling programs from source code isn't the easiest way to install software, and using the package manager instead will save you from loads of manual work, and make managing your programs and updating them a lot easier.

Installing from source allows the software to be installed in any Linux distribution, and also allows one to modify the program code and select different options and optimizations in the process. Most of the time programmers provide the source code in their web pages, and then maintainers of Linux distributions take that code, compile it and then package it for distributing to normal users through package management.

---

### Post by Liberty or Death on 2009-06-30
> **mcduck said:**
> No, they were made for Linux, but not specifically for Ubuntu, they are in the most basic format a program can be (the original source code the programmer wrote when making the program) and can be compiled into a working program that runs on any Linux version.

It's just that compiling programs from source code isn't the easiest way to install software, and using the package manager instead will save you from loads of manual work, and make managing your programs and updating them a lot easier.
Great, that will be easier, I have no experience with source code...:D

---

