---
title: "New user in ubuntu have some question?"
date: 2010-02-25
forum: General Help
---

### Post by uioiuq on 2010-02-25
[FONT=Arial][SIZE=2]**Let me first send a big thanks to all wonderful people who work on this masterpiece.**

I just installed ubuntu 9.10 as a program on winxp sp2, and I have a few questions

1/ Did all Linux os  ( [/SIZE][/FONT][FONT=Arial][SIZE=2]ubuntu , fedora and other ) all are the same with different [/SIZE][/FONT][FONT=Arial][SIZE=2]themes.
2/ are there difference if I install ubuntu as a program on xp or from boot CD.
3/ how can I increase the ubuntu space from 3GB to 5GB cuz it almost full.
5/ what the extension the ubuntu soft I know .exe in MS os and should I search ( soft for ubuntu ) or ( soft for Linux )
4/ I download RealPlayer10GOLD.bin when try to open say ( No application is registered as handling this file ) I use Alt+F2 and enter ( RealPlayer10GOLD.bin )

**thats all for now, thanks**
[/SIZE][/FONT]

---

### Post by MelDJ on 2010-02-25
1. no. they might defer in package management and other areas
2. yes. if you install it as a program, you don't to use the features of the ext filesystem
3. i THINK you must do a reinstall
4. see: [https://help.ubuntu.com/community/RealPlayerInstallationMethods](https://help.ubuntu.com/community/RealPlayerInstallationMethods)
5. ?

---

### Post by encompass on 2010-02-25
> **uioiuq said:**
> [FONT=Arial][SIZE=2]**Let me first send a big thanks to all wonderful people who work on this masterpiece.**

I just installed ubuntu 9.10 as a program on winxp sp2, and I have a few questions

1/ Did all Linux os  ( [/SIZE][/FONT][FONT=Arial][SIZE=2]ubuntu , fedora and other ) all are the same with different [/SIZE][/FONT][FONT=Arial][SIZE=2]themes.

2/ are there difference if I install ubuntu as a program on xp or from boot CD.

3/ how can I increase the ubuntu space from 3GB to 5GB cuz it almost full.
5/ what the extension the ubuntu soft I know .exe in MS os and should I search ( soft for ubuntu ) or ( soft for Linux )
4/ I download RealPlayer10GOLD.bin when try to open say ( No application is registered as handling this file ) I use Alt+F2 and enter ( RealPlayer10GOLD.bin )

**thats all for now, thanks**
[/SIZE][/FONT]

It's more than just themes when you get to the details.  But for beginners I would just stick with ubuntu and try the more advanced ones when you get used to one. Some are built with a specific purpose in mind.  Some for desktops, some for netbooks, some for laptops, some for old and some for now, some for red and some for blue. :P
It seems you have installed ubuntu with the wubi installer.  Though this is good for testing it, I wouldn't recommend it in the long run.  For reasons like you have stated, (Space).  Installing on the harddrive is MUCH faster, uses less ram and you can install and customize to your hearts content.
Files don't really need extensions in linux.  They are simply declared as executable with a command.  It may also be good to note that nothing you get directly from the net is executable in linux.  It must be made executable.  This is a longer discussion that google can answer. :D
Odds are what ever you need is going to already in the repositories.  Don't look for what the name is, look for what you want to do. Like instead of "Photoshop" look for "Image Editor".  A good place to start is the Ubuntu Software Center found by clicking on Applications.  Lots of stuff to look at there.  You can install stuff the "windows way" but it's annoying when you realise how easy life is with a repository.  And you really don't need realplayer if you have something like Totem (Movie player).

---

### Post by uioiuq on 2010-02-27
so thanks for your kindness ( _[COLOR=Black][MelDJ & ]("http://ubuntuforums.org/member.php?u=882795")[encompass]("http://ubuntuforums.org/member.php?u=56215")[/COLOR]_ 				) 				, I'll try it for a bit then install it on a drive but need two more question.

1/ I have two Drives C: & D: one for XP other MyData can I install ubuntu on on D: and keep all my data or should i make a new drive.
2/ My friend tell me that there are no virus for ubuntu so I give it a try, Is that true?

thanks

---

### Post by gjoellee on 2010-02-27
> **uioiuq said:**
> [FONT=Arial][SIZE=2]**Let me first send a big thanks to all wonderful people who work on this masterpiece.**

I just installed ubuntu 9.10 as a program on winxp sp2, and I have a few questions

1/ Did all Linux os  ( [/SIZE][/FONT][FONT=Arial][SIZE=2]ubuntu , fedora and other ) all are the same with different [/SIZE][/FONT][FONT=Arial][SIZE=2]themes.
2/ are there difference if I install ubuntu as a program on xp or from boot CD.
3/ how can I increase the ubuntu space from 3GB to 5GB cuz it almost full.
5/ what the extension the ubuntu soft I know .exe in MS os and should I search ( soft for ubuntu ) or ( soft for Linux )
4/ I download RealPlayer10GOLD.bin when try to open say ( No application is registered as handling this file ) I use Alt+F2 and enter ( RealPlayer10GOLD.bin )

**thats all for now, thanks**
[/SIZE][/FONT]

1. Nope. Different distributions may differ very much in all areas, from the boot process to mail apps.

2. Yes. You won't get the performance boost of the ext filesystem. You are likely to get unnecessary.

3. You can use a program like "gparted"

4. If you put the real player file in your home folder (/home/username) you can launch it by using ```
./RealPlayer10GOLD.bin
``` (I think. I don't have Linux right now so I cannot assure you)

---

### Post by encompass on 2010-02-28
> **uioiuq said:**
> so thanks for your kindness ( _[COLOR=Black][MelDJ & ]("http://ubuntuforums.org/member.php?u=882795")[encompass]("http://ubuntuforums.org/member.php?u=56215")[/COLOR]_ 				) 				, I'll try it for a bit then install it on a drive but need two more question.

1/ I have two Drives C: & D: one for XP other MyData can I install ubuntu on on D: and keep all my data or should i make a new drive.
2/ My friend tell me that there are no virus for ubuntu so I give it a try, Is that true?

thanks

_Drive letters are something made up bythe old Dos days.  They have nothing to do with the physical drives in your computer.
You can howeever, delete drive D and put linux on it.
Linux have very few if any viruses.  This is true,.. but if you have installed linux inside of windows, a virus could destroy uyour linux installation from windows.  That is why I recommend installing on a spare diver or section (called a partition) of a drive.  If you have a drive D you can erase it and install there.

---

### Post by uioiuq on 2010-03-01
**thanks alot all of you...**

---

### Post by 3rdalbum on 2010-03-01
You don't need Realplayer. If you install the "w32codecs" package you will gain the ability to play Realplayer content in all your media players.

Secondly, on Linux you don't trawl the web to find and download software. You look in your package manager for software. Applications > Ubuntu Software Center is a good place to start.

If you want software that is not in your default set of repositories, you can do a Google search for an Ubuntu repository or PPA containing the program you want. For instance, you could do a search for "Flash player PPA" (although Flash Player is in the default repositories - just an example).

If you install Ubuntu using the Windows-based installer, your Ubuntu system is twice as fragile because if Windows crashes and will no longer boot up, then you can't boot Ubuntu either. I'll also add that 3 gigabytes and 5 gigabytes are too small for Ubuntu - the system requirements say you should have a minimum of 4 gigabytes of space.

Why not install Ubuntu the proper way, by booting up your computer from the CD and running the Install program in Ubuntu? I'd recommend giving 10 gigabytes or more. The installer will help you resize your Windows partition, or you can choose to put your "/" onto a different disk. ("/" is basically the Ubuntu system - you'll need to remember this for the manual partitioning step, if you decide to do this).

Installing Ubuntu will involve reformatting a hard disk or partition, depending on where you decide to put it. So no, you can't keep your existing Windows data on the same hard disk unless you partition the drive. The Ubuntu installer will help you to resize a partition to create space for Ubuntu.

---

### Post by uioiuq on 2010-03-04
so if i install ubuntu as a program on xp dose that harm my hard disk by compress files when i shutdown ubuntu and decompress files when i start ubuntu, thanks

---

