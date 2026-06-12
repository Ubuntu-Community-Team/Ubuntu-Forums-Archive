---
title: "Fixing MBR using livecd?"
date: 2010-07-05
forum: General Help
---

### Post by KowalPL on 2010-07-05
Hi,

First my situation. I had a genious idea to remove my exisitng Ubuntu partition in order to gain on hard drive space. In order to achieve this I have also very intleignetly used Partition Magic 8 from Windows and set it to format Ubuntu partition and its swappartition into NTFS. 

Now the problem. Every time the PC boots, GRUB loads up (1.97~beta4) and tells me to make a choice between whatever the options are (Ubuntu versions and their recovery modes + Windows and memtest). Whatever option I choose I get error: no file found. Not eve a single command works from grub console. 

I was reading around the net. There was a lot of guides and how to's however none of them worked as they were supposed to. There was a fix that started with 'sudo grub' which then goes onto checking where my partition is (0,0) etc. From this I get grub command not found. There were also solutions to this but still to no avail. 

**sudo apt-get install ms-sys**  fix doesn't work either (can't find ms-sus package) probably because it was a fix for 7.x version and I am running 9.1 livecd.

Thank you for any replies.

Quick Edit:
Removing the GRUB itself in order to get access to Windows OS is fine.

---

### Post by WorMzy on 2010-07-05
If you have your Windows CD, booting that and getting it to fix the mbr is probably your best bet. Or else you can manually download and compile ms-sys from here: [http://sourceforge.net/projects/ms-sys/](http://sourceforge.net/projects/ms-sys/)

---

### Post by KowalPL on 2010-07-05
Hi thanks for fast answer

I don't have Windows CD or I'd be done with it by now ;S

About compiling ms-sys exactly how do I do that ;S My knowledge about Ubuntu is really small ;P

Edit:
Nvmd README is always useful... Except that it asks me for a passowrd when using 'su' command but I thought you don't need a password when using livecd?

---

### Post by WorMzy on 2010-07-05
You don't, the readme isn't optimised for LiveCDs or Ubuntu in general, just substitute any mention of su with sudo, you won't be prompted for a password.

---

### Post by KowalPL on 2010-07-05
So yeah I couldn't unpack the archive using commadn in readme so I jsut used archive manager. After that I had to install gettext because make would not work porperly. Anyway I followed the isntructions to my best and could not get it to work(?) I don't knwo what it is supposed to do anyways the readme talks about putting stuff on floppys etc :S Confusing

---

### Post by philinux on 2010-07-05
To fix windows MBR without a windows cd see section #16.

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by WorMzy on 2010-07-05
Downloaded it myself and compiled, using --help as an argument to the program tells you how to use it. Basically:

sudo ms-sys -m /dev/sda #for Windows 2000/XP/2003
OR
sudo ms-sys -i /dev/sda #for Windows Vista
OR
sudo ms-sys -7 /dev/sda #for Windows 7

Substituting sda for the disk you want to install the bootloader to. Philinux's post suggests using lilo in a similar way, that's probably a better approach since lilo is Canonical approved and in the repos.

---

