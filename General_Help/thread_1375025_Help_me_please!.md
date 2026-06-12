---
title: "Help me please!"
date: 2010-01-07
forum: General Help
---

### Post by XLAWLX on 2010-01-07
Hi, i got a external hard drive for christmas and i installed ubuntu on it. then i couldent boot in to anything if the USB wasent pluged in because of GRUB so i removed GRUB and now i cant see my external USB drive in windows to formate it please someone help me!!

Computer:
Toshiba 
Windows Vista

External Hard Drive: HP Simple Save

---

### Post by nothingspecial on 2010-01-07
> **XLAWLX said:**
> Hi, i got a external hard drive for christmas and i installed ubuntu on it. then i couldent boot in to anything if the USB wasent pluged in because of GRUB so i removed GRUB and now i cant see my external USB drive in windows to formate it please someone help me!!

Computer:
Toshiba 
Windows Vista

External Hard Drive: HP Simple Save

Have a look at [[COLOR="Magenta"]this[/COLOR]]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

And take note of my sig ;)

---

### Post by XLAWLX on 2010-01-08
No no i want to get to my external hard drive its not letting me

---

### Post by nothingspecial on 2010-01-08
Question 1:   Do you want a ubuntu install?

Question 2:   Does it have to be on the external drive?

The reason I ask is that Ubuntu only needs 6-8 gigs and it would be better to install it straight to your computer and use the external drive as a data drive shared between the 2 operating systems.

If you don`t want ubuntu and just want to reformat the drive this is possible.

So, Ubuntu?......external or internal?........or just windows and a reformatted drive?

---

### Post by XLAWLX on 2010-01-09
no no buddy,

i installed ubuntu on my external hard drive.

then i took GRUB off my PC because it wasent letting me get in to vista so i did the master boot record thing to get in to vista..now my external hard drive wont be recognized in my vista.

Thanks

---

### Post by nothingspecial on 2010-01-09
[SIZE="3"][COLOR="Red"]These instructions will completely wipe your ubuntu installation from your external drive and any data contained within it[/COLOR][/SIZE]


Ok, if you have a Ubuntu live cd (if you don`t, download and burn one), boot it up.

Plug in your hard drive.

In the menu, go system > administration > partition editor (it might be called gparted now)

In the top right will be a dropdown box allowing you to select which drive you want to format/partition.

**[COLOR="Red"][SIZE="3"]MAKE SURE YOU CHOOSE THE CORRECT ONE[/SIZE][/COLOR]**

If you are unsure, in the menu go applications > accessories > terminal and type ```
sudo fdisk -l
``` The last character is a little L not a number one ;)

You should be able to figure out which device lable (/dev/sd??) is your external from the size.

When you are sure you have selected the correct one, right click on the long box just below the top horizontal tool bar. It will probably be /dev/sdb1 but I can`t impress on you enough - make sure it`s the correct one.

Choose format to - and select which file system you want. (probably ntfs or fat? if you want to use it with windows)

I know I`ve said this twice before but -

[COLOR="Red"][SIZE="3"]If you get this wrong you could erase all your data, windows and everything[/SIZE][/COLOR]

Might be an idea to backup first.

---

