---
title: "increasing disc space"
date: 2010-12-14
forum: General Help
---

### Post by Angelbrand on 2010-12-14
im going crazy. i have 32gb of unused space that i got after shinking a partion on vista (i use dual vista/ubuntu)

i need to increase my ubuntu disc space but i cannot find a way to do it. i tried to download gparted but it was a waste of time as it doesnt even register as a program just a bunch of useless files! i have absolutely no space left please some on help me!


i have four volumes showing in ubuntus disc utility

WinRE 6.3gb ntfs                 OS_Install 37gb ntfs                        Data 82gb ntfs                               Free Space32gb

---

### Post by drs305 on 2010-12-14
Angelbrand,

Welcome to the Ubuntu forums.

You can probably make a bit of space by opening a terminal (Applications, Accessories, Terminal) and then running this command. It will remove downloaded packages which have been installed and are no longer needed:
```
sudo apt-get clean
```
You will be asked for your password. You won't see it as you type.

This should free up space, so try installing Gparted again:
```
sudo apt-get install gparted
```

If you can get it installed, you can review this post about expanding your / partition.
[http://ubuntuforums.org/showthread.php?t=1219270]("http://ubuntuforums.org/showthread.php?t=1219270")

See also *srs5694's* link at the bottom of that page.

---

### Post by Quackers on 2010-12-14
Welcome to UF
Go to System > Admin > Synaptic Package Manager and in the search box enter gparted. The program will appear in the main panel. Right-click it and select mark for installation. In the confirmation box click on Mark. Click on the green tick in the toolbar to apply the changes. Confirm by clicking on Apply. When the program is installed go to System > Admin > Gparted.
Please post a screenshot of that screen in your next post.

Edit: drs305 can type faster :-)

---

### Post by Angelbrand on 2010-12-14
thank you! 

what partition is ubuntu?

i know the os install is vista..

---

### Post by SoftwareExplorer on 2010-12-14
I only see NTFS partitions. I don't think ubuntu can be installed on one unless you used WUBI. 
So, there's probably two options:
You used wubi, or 
It's installed on a different physical disk (i.e. you have two hard disks).

If you have it on a different disk, you could look at that disk using the menu in the upper right corner of the program (it probably says something like /dev/sda right now).

If you installed using WUBI, giving Ubuntu more space will be a little different because Ubuntu is actually installed inside the windows filesystem/partition.

---

### Post by Angelbrand on 2010-12-14
i used wubi

---

### Post by SoftwareExplorer on 2010-12-14
I would recommend taking a look at:
[[COLOR="DeepSkyBlue"]http://lubi.sourceforge.net/lvpm.html[/COLOR]]("http://lubi.sourceforge.net/lvpm.html")
[[COLOR="DeepSkyBlue"]https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?[/COLOR]]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?")

I've only resized a WUBI install once, so hopefully other forumites can give you help if you need it.

---

### Post by Angelbrand on 2010-12-14
thanks for the help guys looks like it'll just be easier to install kubuntu... and get rid of wubi..

---

### Post by SoftwareExplorer on 2010-12-14
I don't want to complicate your decision making process or anything, but you can install kubuntu on ubuntu by running ```
sudo apt-get install kubuntu-desktop
``` in a terminal. (Which would definitely take more space than just ubuntu, so you would have to do it after resizing WUBI or moving ubuntu into it's own partition.)

---

### Post by Angelbrand on 2010-12-14
its to complicated to resize so im deleting ubuntu..

---

