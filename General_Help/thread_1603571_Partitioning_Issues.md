---
title: "Partitioning Issues"
date: 2010-10-22
forum: General Help
---

### Post by MicrobatX on 2010-10-22
I have been trying to take anywhere from 22GB to 50GB of memory from my windows partition and place it onto my ubuntu partition. I've tried doing it from gparted, I've tried using the command line, I've tried many things. I can't write files to disks on Ubuntu currently and I nuked all my programming files on windows (That was a stupid idea...but it still freed 60GB...I need to reinstall things to use the internet on it now). And as it turns out, my system is detecting my Ubuntu partition as an entirely different disk from what Disk utility is saying. 

And as a note, any time I attempt to unmount my windows partition from Gparted I get an error stating its busy; Using Disk Utility states its mounted twice. 

As a final note, I have Mandriva, Ubuntu, and Windows Vista installed on this computer. Can someone tell me how to fix this? I'm thinking I need to reinstall Ubuntu, and get rid of Mandriva, not in that particular order...

---

### Post by jerrrys on 2010-10-23
first off did you defrag vista before you started this?  second i would partition vista with a vista partition editor and not use gparted.  use to be a bug about this, don't know if it ever got fixed.  and last info on partitioning can be found here

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=how+to+partition+vista+ubuntu&as_qdr=all&sa=Google+Search&lang=en#1059](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=how+to+partition+vista+ubuntu&as_qdr=all&sa=Google+Search&lang=en#1059)

a word of caution..
your going to be messing with your grub/mbr (boot).  do a little reading first, it's easy to mess things up

and welcome to the forum :)

---

### Post by perspectoff on 2010-10-23
Yeah, you can nuke Windows Vista by shrinking its partition using GParted.

I don't know a way to fix it if you do (aside from re-installing Windows).

Further, if Windows is "busy" (either because it is in hibernation mode or because it has been nuked), it is not that easy to recover files from it, even from Linux. 

Hope you backed up beforehand.

BTW, what's with all the googlubuntu links that are empty?

---

### Post by Quackers on 2010-10-23
If you are using Vista or W7 it is much easier/quicker/safer to go to Start > right-click on Computer and select Manage > Disk Management. You then get a screen showing your disk layout. Right-click on the Vista or W7 partition and select Shrink. It does have some limitations as to size but it is the safest way imo.

---

### Post by jerrrys on 2010-10-23
> **perspectoff said:**
> BTW, what's with all the googlubuntu links that are empty?

What :confused:  im not seeing this, please elaborate

---

### Post by oldfred on 2010-10-23
Anyone with multiple systems or multiple drives should run this script before & after making changes just to document how system is set up.

So we all know exactly what is where:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by coffeecat on 2010-10-23
> **perspectoff said:**
> Yeah, you can nuke Windows Vista by shrinking its partition using GParted.

I don't know a way to fix it if you do (aside from re-installing Windows).

Here you go. A complete guide to making Vista unbootable with Gparted and how to repair it afterwards with the "repair your computer" utility on the  Vista install DVD:

[http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/](http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/)

And if you don't have a Vista install DVD, where to get a Vista Recovery CD which will do the same job:

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

---

### Post by MicrobatX on 2010-10-26
I've tried to resize my windows partition in windows a few times...didn't seem to work. I can't resize it with gparted, I can't resize it using ntfsresize...So I'm going to attempt using the Gparted Live CD... I backed up my files. Wish me luck.

---

### Post by MicrobatX on 2010-10-30
And...after a few days, I finally have my computer back up and running Ubuntu...Thanks.

---

