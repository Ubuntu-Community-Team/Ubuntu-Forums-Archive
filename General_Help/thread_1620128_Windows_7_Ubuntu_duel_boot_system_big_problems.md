---
title: "Windows 7 Ubuntu duel boot system big problems"
date: 2010-11-12
forum: General Help
---

### Post by floydcat on 2010-11-12
[FONT=Times New Roman][SIZE=3][FONT=Microsoft Sans Serif]Please help!!![/FONT][/SIZE][/FONT]
 
[SIZE=3][FONT=Microsoft Sans Serif][FONT=Times New Roman]I am a complete noob to Linux earlier this week I installed [/FONT][FONT=Microsoft Sans Serif]**Ubuntu 9.10 onto my Samsung N210 netbook running windows 7 starter (it did not come with any disks I just had to make a recovery area on the hard drive) to run as a duel boot system. After installation I booted up Ubuntu a couple of times and everything was fine, I then tried to boot into windows 7 and it did not work. System recovery came up and wanted me to A recover basic windows settings or B complete system restore. I chose neither and decided to cancel. I then decide to reboot and all that happened was the Samsung splash screen came up for a couple of seconds, then a black screen with GRUB came up for a couple of seconds this continued in a rotation and I could do nothing else. The F4 button (which is used to activate Samsung system restores) did not work. **[/FONT][/FONT][/SIZE]
 
[FONT=Microsoft Sans Serif]**[SIZE=3][FONT=Microsoft Sans Serif]Big panic I now had a pc that would not run windows or Linux.[/FONT][/SIZE]**[/FONT]
 
[SIZE=3][FONT=Microsoft Sans Serif][FONT=Microsoft Sans Serif]**I used the works laptop and checked out some forums which told me to download **[/FONT][FONT=Microsoft Sans Serif]**AdminTool_for_SRS4.iso which I could use to reinstate the F4 system restore function. Unfortunately I am currently working out in Africa (and not due back to Scotland for a couple of weeks) and the bandwidth and constant drop outs of connection made it impossible to download this.**[/FONT][/FONT][/SIZE]
 
[FONT=Microsoft Sans Serif]**[SIZE=3][FONT=Microsoft Sans Serif]I used my Linux installation usb stick and formatted the drives with Ubuntu and Linux-swap on them then reinstalled Ubuntu. It worked.[/FONT][/SIZE]**[/FONT]
 
[FONT=Microsoft Sans Serif]**[SIZE=3][FONT=Microsoft Sans Serif]I stopped panicking a little bit.[/FONT][/SIZE]**[/FONT]
 
[FONT=Microsoft Sans Serif]**[SIZE=3][FONT=Microsoft Sans Serif]I tried booting Ubuntu a couple of times and it worked. I then tried booting into windows and again it did not work but system restore started up (good times) I chose option A recover basic windows settings then rebooted.[/FONT][/SIZE]**[/FONT]
 
[FONT=Microsoft Sans Serif]**[SIZE=3][FONT=Microsoft Sans Serif]The same thing happened again with the Samsung splash screen and the GRUB screen (Bad Times).[/FONT][/SIZE]**[/FONT]
 
[SIZE=3][FONT=Microsoft Sans Serif][FONT=Microsoft Sans Serif]**Again I **[/FONT][FONT=Microsoft Sans Serif]**used my Linux installation usb stick and formatted the drives with Ubuntu and Linux-swap on them then reinstalled Ubuntu. Then when I tried to load windows same thing again Samsung recovery started and I chose option B complete system recovery from image.**[/FONT][/FONT][/SIZE]
 
[FONT=Microsoft Sans Serif]**[SIZE=3][FONT=Microsoft Sans Serif]I rebooted and at this point I actually thought that windows would run properly.[/FONT][/SIZE]**[/FONT]
 
[FONT=Microsoft Sans Serif]**[SIZE=3][FONT=Microsoft Sans Serif]Silly me, same thing again Samsung splash screen and the GRUB screen (Very Bad Times).[/FONT][/SIZE]**[/FONT]
 
[FONT=Microsoft Sans Serif]**[FONT=Microsoft Sans Serif][SIZE=3]So I reformatted and reinstalled Ubuntu again. I then tried Google for information again (on my work laptop) and found out about the SUPER GRUB DISK from [/SIZE][/FONT][[FONT=Microsoft Sans Serif][SIZE=3][COLOR=#800080]www.supergrubdisk.org[/COLOR][/SIZE][/FONT]]("http://www.supergrubdisk.org/")[SIZE=3][FONT=Microsoft Sans Serif] which from reading forums I understand should enable me to boot back into windows. I followed the instructions on this website to create a bootable USB stick pen of SGD from Ubuntu unfortunately because I am such a noob to Linux it did not work (operator error I think) I have since found out from forums that I think I should of downloaded super grub disk 2 to use with Ubuntu 9.10?[/FONT][/SIZE]**[/FONT]
 
[FONT=Microsoft Sans Serif]**[SIZE=3][FONT=Microsoft Sans Serif]At present my HDD is setup up like this partition 1 windows 7 recovery image partition 2 windows loader partition 3 C drive? Partition 4 D drive (small partition for extra data to be stored) all these drives are NTFS system? Partition 4 Ubuntu system software? Partition 5 Linux-swap software.[/FONT][/SIZE]**[/FONT]
 
[FONT=Microsoft Sans Serif]**[SIZE=3][FONT=Microsoft Sans Serif]Just to recap I have a windows 7 operation system that will not boot and a Ubuntu operating system that works but wireless does not work (I have seen this on forums and will deal with it later, but I don’t have any wired connection options only wireless or MTN mobile dongle that does not work either).[/FONT][/SIZE]**[/FONT]
 
[FONT=Microsoft Sans Serif]**[SIZE=3][FONT=Microsoft Sans Serif]First of all I would like to thank anybody who has taken the time and effort to read through this long winded post. I was just trying to include every bit of information.[/FONT][/SIZE]**[/FONT]
 
[FONT=Microsoft Sans Serif]**[SIZE=3][FONT=Microsoft Sans Serif]Second what do I think I need?[/FONT][/SIZE]**[/FONT]
 
[FONT=Microsoft Sans Serif]**[SIZE=3][FONT=Microsoft Sans Serif]I would like to be able to boot back into windows. Exact step by step very noob instructions on how to make a bootable SGD / 2 usb stick pen from Ubuntu (if you think this will help me). Any other information which anyone thinks would be relevant to help me.[/FONT][/SIZE]**[/FONT]
 
[FONT=Microsoft Sans Serif]**[SIZE=3][FONT=Microsoft Sans Serif]These problems have not put me of from Linux I just want them sorted then I will try again hopefully with better results[/FONT][/SIZE]**[/FONT]
 
[FONT=Microsoft Sans Serif]**[SIZE=3][FONT=Microsoft Sans Serif]Thank you[/FONT][/SIZE]**[/FONT]
[FONT=Microsoft Sans Serif]**[SIZE=3][FONT=Microsoft Sans Serif]Floydcat[/FONT][/SIZE]**[/FONT]

---

### Post by wilee-nilee on 2010-11-12
Post the bootscript in my signature. Post it in code tags by, opening a reply click on the # in the reply panel you will see code tags appear paste the text from the generated file from running the script in between.

---

### Post by Hippytaff on 2010-11-12
ok...so if you can boot into ubuntu open a terminal (ALT+F2) ant type
```

sudo update-grub

```
you might need to enter your password (don't panic  when you type your password and nothing appears as you type - this is normal)

also - if you can boot into ubuntu run this script and flollow the instructions :-)
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

we're her for you :-)

---

