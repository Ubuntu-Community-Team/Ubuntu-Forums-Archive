---
title: "I have Installation Problems"
date: 2009-10-20
forum: General Help
---

### Post by wapotter on 2009-10-20
[FONT=Times New Roman][SIZE=3]I installed Ubuntu 9.04 (i386) for the first time on my computer last month, and I'm never switching back to windows. I'd like you to help me solve the following problems.[/SIZE][/FONT]
 
[FONT=Times New Roman][FONT=Nimbus Roman No9 L][SIZE=3]1.[/SIZE] [/FONT][SIZE=3]How can I install and run a windows (.exe) application, add its (.dll) plug-ins and other add-ons?How can I use a windows (.exe) application which doesn't have an installer that can run from a folder, such as the Mame32 emulator and the Revolt game?[/SIZE][/FONT]
[FONT=Times New Roman][FONT=Nimbus Roman No9 L][SIZE=3]2.[/SIZE] [/FONT][SIZE=3]How can I install a Linux application, or its patch, if its package (not the .deb packages) is stored inside a hard drive or a removable media as a tar.gz or tar.bz2? When I try to follow instructions it sounds too geeky to me.[/SIZE][/FONT]
[FONT=Times New Roman][FONT=Nimbus Roman No9 L][SIZE=3]3.[/SIZE] [/FONT][SIZE=3]Whenever I insert a CD/DVD in the CD/DVD-ROM drive I can't access any item on the Places menu (even though the list appears when I click on the menu and items). Secondly, all drives, partitions and folders get automatically unmounted. Thridly, the CD/DVD-ROM drive freezes when there is a CD/DVD inside, .i.e. when I press the eject button on the drive nothing happens unless I restart the computer. How can I browse content inside a CD/DVD with the default file manager like I do with a removable media?[/SIZE][/FONT]
[FONT=Times New Roman][FONT=Nimbus Roman No9 L][SIZE=3]4.[/SIZE] [/FONT][SIZE=3]When I insert an audio CD I get the message: Could not open location 'cdda://sro/' failed to execute child process “ sound juicer” (no such file or directory). What does this mean?[/SIZE][/FONT]
[FONT=Times New Roman][FONT=Nimbus Roman No9 L][SIZE=3]5.[/SIZE] [/FONT][SIZE=3]How can I install the NVIDIA-Linux-x86-173.14.20-pkg1.run driver, [www.nvidia.com]("http://www.nvidia.com") instructs me to type “sh NVDIA-LINUX-X86-173.14.20.pkg1.run” to install it? How can I do this? :-I’m new to Linux.[/SIZE][/FONT]
 
[FONT=Times New Roman][FONT=Nimbus Roman No9 L][SIZE=3]6.[/SIZE] [/FONT][SIZE=3]I downloaded a Gimp fonts freefonts-0.10.tar.gz package which has an installation guide that reads: [/SIZE][/FONT]
 

[SIZE=3][FONT=Times New Roman]Installation for X11 [/FONT][/SIZE]
[LIST]
[*][SIZE=3][FONT=Times New Roman]**Change to /usr/X11/lib/fonts** [/FONT][/SIZE]
[*][SIZE=3][FONT=Times New Roman]**Untar the archive freefonts-0.10.tar.gz** {*How?*} [/FONT][/SIZE]
[*]**[SIZE=3][FONT=Times New Roman]Give the the follwing commands to make X11 accept the new fonts[/FONT][/SIZE]**
[/LIST]**[SIZE=3][FONT=Times New Roman]xset fp+ /usr/X11/lib/fonts/freefont[/FONT][/SIZE]**

**[SIZE=3][FONT=Times New Roman]xset fp rehash[/FONT][/SIZE]**
[LIST]
[*][SIZE=3][FONT=Times New Roman]**The fonts are available under X11.** [/FONT][/SIZE]
[/LIST]**[SIZE=3][FONT=Times New Roman]Check them out by running “xfontsel” for example. [/FONT][/SIZE]**
 

[SIZE=3][FONT=Times New Roman]Installation for Ghostscript [/FONT][/SIZE]
[LIST]
[*]**[SIZE=3][FONT=Times New Roman]Change to /usr/lib/ghostscript [/FONT][/SIZE]**
[*][SIZE=3][FONT=Times New Roman]**Save the file “Fontmap” **{*What's a Fontmap file?*}[/FONT][/SIZE]
[*][SIZE=3][FONT=Times New Roman]**e.g. cp Fontmap Fontmap.old **{*Do I have to type this command?*}[/FONT][/SIZE]
[*]**[SIZE=3][FONT=Times New Roman]Copy the new Fontmap from the archive [/FONT][/SIZE]**
[/LIST]**[SIZE=3][FONT=Times New Roman]If you have installed it already in X11 do[/FONT][/SIZE]**

**[SIZE=3][FONT=Times New Roman]cp /usr/lib/fonts/freefont/Fontmap[/FONT][/SIZE]**
[LIST]
[*]**[SIZE=3][FONT=Times New Roman]Copy necessary fonts to the ghostscript directory[/FONT][/SIZE]**
[/LIST][SIZE=3][FONT=Times New Roman]**(or use links) **{*How to use links?*}[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]**cp /usr/libs/freefont/tempo*pfb font**[/FONT][/SIZE][SIZE=3][FONT=Times New Roman]** cp /usr/libs/freefont/baskvl*pfb font **{*Do I have to copy all of them individually?*}[/FONT][/SIZE]
 
[FONT=Times New Roman][SIZE=3]Is this how all .pfb and .ttf gimp/Ubuntu fonts are installed? Are we always required to install fonts into both directories? In my Filesystem directory pre-installed .pfb files are stored in the /usr/share/fonts/X11/Type1, /usr/share/fonts/type1/gsfonts and /var/lib/defoma/gs.d/dirs/fonts directories, is this where all fonts are automatically stored once they are installed? How can I install fonts in GUI, as a root user?[/SIZE][/FONT]

---

### Post by John Bean on 2009-10-20
That's a lot of questions, but let's just look at the first one. There are several approaches, this is what you perhaps could try first:

[http://www.lmgtfy.com/?q=how+to+run+windows+programs+on+ubuntu](http://www.lmgtfy.com/?q=how+to+run+windows+programs+on+ubuntu)

Google is your friend ;-)

---

### Post by philinux on 2009-10-20
[http://ubuntuforums.org/showthread.php?p=8109167#post8109167](http://ubuntuforums.org/showthread.php?p=8109167#post8109167)

Best way to solve your problems is to post one thread per problem.

---

### Post by junglist313 on 2009-10-20
Mame runs on linux, I use kxmame as the frontend
```
sudo apt-get install kxmame
```

---

