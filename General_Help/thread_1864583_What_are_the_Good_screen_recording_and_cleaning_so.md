---
title: "What are the Good screen recording and cleaning software"
date: 2011-10-19
forum: General Help
---

### Post by Udagama on 2011-10-19
[SIZE=2]Hi!
[/SIZE]
[LIST]
[*][SIZE=2]I want to know what are the easy to use Ubuntu screen recording free softwares. [/SIZE]
[*][SIZE=2]And also what are the good computer defraging and cleaning softwares for Ubuntu like Ccleaner and smart defrag for windows OS.[/SIZE]
[/LIST]
[SIZE=2]
Thanks![/SIZE]

---

### Post by TeoBigusGeekus on 2011-10-19
1) [http://www.foresightlinux.se/en/blog]("http://www.foresightlinux.se/en/blog")

2) For a CCleaner equivalent, look at bleachbit; it's in the software centre.
Using a linux filesystem (ext3, ext4, etc.) you don't need to defragment your hard drive.

---

### Post by Erik1984 on 2011-10-19
RecordMyDesktop can be found in the software center

---

### Post by bryncoles on 2011-10-19
Hi There Udagama. 

For recording the screen (screencasting?) I have in the past made use of a little thing called 'recordmydesktop'.  I recommend the **gtk-recordmydesktop** package, as it comes with a friendly GUI too.  I have then made clumsy attempts to edit the resulting video file with **avidemux**.  I guess you could also try pitivi (for editing), though I've never used that so couldn't vouch for it.  

As for cleaning / defragging your computer, TeoBigusGeekus is correct.  ext3 / ext4 file systems are apparently not as prone to fragmentation as NTFS and FAT32, so you shouldn't worry about that.  You could try running in the terminal the commands 

```
sudo apt-get autoclean
sudo apt-get autoremove
```
to clean out packages which are lingering on your computer, which you no longer need I suppose.  That's about the only cleaning I do with my Ubuntu!

---

### Post by haqking on 2011-10-19
> **Udagama said:**
> [SIZE=2]Hi!
[/SIZE]
[LIST]
[*][SIZE=2]I want to know what are the easy to use Ubuntu screen recording free softwares. [/SIZE]
[*][SIZE=2]And also what are the good computer defraging and cleaning softwares for Ubuntu like Ccleaner and smart defrag for windows OS.[/SIZE]
[/LIST]
[SIZE=2]
Thanks![/SIZE]

Kazam or recordmydesktop

And as mentioned above you dont need to defrag  as Linux filesystems are not as prone to it as others, as for cccleaner equivalents yes there is bleachbit but remember there is no registry per se in Linux.

---

### Post by Udagama on 2011-11-09
> **TeoBigusGeekus said:**
> 1) [http://www.foresightlinux.se/en/blog](http://www.foresightlinux.se/en/blog)

2) For a CCleaner equivalent, look at bleachbit; it's in the software centre.
Using a linux filesystem (ext3, ext4, etc.) you don't need to defragment your hard drive.

Ok thinks buddy, I'll try them, but we we need not defragment hard disk? I have no idea! :D

> **Euroman said:**
> RecordMyDesktop can be found in the software center

Thanks friend. I'll try it. :D

> **bryncoles said:**
> Hi There Udagama.

For recording the screen (screencasting?) I have in the past made use of a little thing called 'recordmydesktop'. I recommend the gtk-recordmydesktop package, as it comes with a friendly GUI too. I have then made clumsy attempts to edit the resulting video file with avidemux. I guess you could also try pitivi (for editing), though I've never used that so couldn't vouch for it.

As for cleaning / defragging your computer, TeoBigusGeekus is correct. ext3 / ext4 file systems are apparently not as prone to fragmentation as NTFS and FAT32, so you shouldn't worry about that. You could try running in the terminal the commands

```
sudo apt-get autoclean
sudo apt-get autoremove
```to clean out packages which are lingering on your computer, which you no longer need I suppose. That's about the only cleaning I do with my Ubuntu!

Thanks buddy reply. Which application better for simple video editing process?

> **haqking said:**
> Kazam or recordmydesktop

And as mentioned above you dont need to defrag as Linux filesystems are not as prone to it as others, as for cccleaner equivalents yes there is bleachbit but remember there is no registry per se in Linux.
Ya i know registry has only windows.

---

