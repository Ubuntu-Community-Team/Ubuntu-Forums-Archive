---
title: "How to remove other os's from ubuntu?"
date: 2009-12-23
forum: General Help
---

### Post by Deathrow_cy on 2009-12-23
I have a dual-booted pc with vista and ubuntu installed. How can i uninstall vista _FROM UBUNTU_ (just like you can uninstall ubuntu from vista) so ubuntu is the only os installed?

Any information will be given if necessary.

---

### Post by chaanakya_chiraag on 2009-12-23
The easiest way is to use something called Gparted:
Go to the terminal (Applications -> Accesories -> Terminal) and enter the following piece of code which will install the package gparted:
```
sudo aptitude install gparted
```
After that installs (you may have to enter your password before it lets you install it) go to System->Administration -> Gparted.  With me so far?  Good :)
Now, if your two os's are on different **hard disks**:
There should be a drop-down box in the upper right hand corner.  Click on that and select the hard drive that "looks correct" ie. it is formatted as NTFS.  Then right-click on each partition that appears and click Delete.  Finally, click the Checkmark (the Apply all operations button).  **WARNING: YOU WILL LOSE ALL DATA ON THE HARD DISK, SO MAKE SURE YOU ARE FORMATTING THE RIGHT ONE**  If you have ANY doubts, I suggest you ASK.  The last thing we need is you losing all your data.  Finally, after that applies, go back to the terminal window and type:
```
sudo update-grub
``` entering your password again if necessary.  This should do the trick.  If there is any confusion or uncertainty, or if you just have any questions, please feel free to ask :)
- Chiraag

---

### Post by Deathrow_cy on 2009-12-24
Well im in gparted, and i see the hard-drive but im not really understanding how i can uninstall vista from there. Sorry for my noobiness. :P

EDIT: Oh sorry i forgot to ask, is it supposed to look like this?

[ATTACH]141017[/ATTACH] <--- Click

---

### Post by Grenage on 2009-12-24
Vista will be installed on another partition (or another hard drive).  Let's assume you have Vista installed on another partition on the same drive.  In gparted you could delete the Vista partition, then expand you ubuntu partition to take up the extra space.

If you do change the ubuntu partition (expand it etc) then you'll need to boot using a linux live CD and run gparted from there.  You cannot resize a mounted partition.

If you don't want to resize, you could simply format the Vista partition to Ext3/4 and add it to your fstab file (so it mounts on boot).

You'll probably also want to take vista out of grub.  If you elaboration, post back.

---

### Post by Deathrow_cy on 2009-12-24
Nope, i dont mind if ubuntu is that size, i just want vista out of the question.

---

### Post by Kevbert on 2009-12-24
Once you've removed the Vista partition, do this.
To get rid of the Vista/Windows menu item when you boot up go to Applications-Accessories-Terminal and enter
```
sudo update-grub 
```
Enter your login password when prompted.

---

### Post by lisati on 2009-12-24
<edit:nevermind I was too slow off the mark>

---

### Post by Deathrow_cy on 2009-12-24
Guys, let me clear things up. I have gparted running. How can i find the vista partition and delete it.

[ATTACH]141019[/ATTACH]

---

### Post by coffeecat on 2009-12-24
@Deathrow_cy, as no one has asked this: did you install Ubuntu using Wubi? Did you follow a procedure like this?

[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

Because, if so, you can't "uninstall Vista from Ubuntu" because Ubuntu is "inside" Vista. You can only remove Vista and leave Ubuntu intact if you did a conventional dual-boot install with Ubuntu on its own dedicated partitions. Your screenshot shows your sda drive wholly occupied with one NTFS partition - which would be your Vista C:\ drive. Is there a second hard disc in that machine, or is that drive the only one?

---

### Post by Deathrow_cy on 2009-12-24
> **coffeecat said:**
> @Deathrow_cy, as no one has asked this: did you install Ubuntu using Wubi? Did you follow a procedure like this?

[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

Because, if so, you can't "uninstall Vista from Ubuntu" because Ubuntu is "inside" Vista. You can only remove Vista and leave Ubuntu intact if you did a conventional dual-boot install with Ubuntu on its own dedicated partitions. Your screenshot shows your sda drive wholly occupied with one NTFS partition - which would be your Vista C:\ drive. Is there a second hard disc in that machine, or is that drive the only one?

I see, theres no way to fix this =\.

---

### Post by SuperSonic4 on 2009-12-24
Vista is not on that drive.

If you have a wubi install backup important files and use a live cd to install ubuntu to the hdd

In gparted check if there is another physical drive. You can also post the output of ```
sudo fdisk -l
``` if you're not sure.

You can use cfdisk to remove a file format although you will have to manually put a filesystem on it

---

### Post by Grenage on 2009-12-24
You can just overwrite the whole machine with a fresh ubuntu install, using the CD.  If you do, just make sure you back things up :)

---

### Post by coffeecat on 2009-12-24
> **Deathrow_cy said:**
> I see, theres no way to fix this =\.

I presume from that you mean that you did install Ubuntu using Wubi. If so, then sorry, no. **Edit**: Just noticed the mountpoint = /host in your screenshot. That's a giveaway. That is a Wubi install.

A little explanation. A "conventional" dual boot would have shrunk your Vista NTFS partition to make room to create two partition for Ubuntu. One swap partition and one 'root' partition formatted with the Linux filesystem ext4. (NTFS is a Microsoft filesystem.)

Wubi creates a file inside C:\ubuntu (this from memory) in which all the Ubuntu stuff goes. Reformat or delete the C: partition and Ubuntu goes up in a puff of smoke.

You do have one option though. If you really want to be rid of Vista, do a 'proper' install. Boot up from the live CD, start the installer and, at the partitioning stage, choose 'use whole disc' (or words to that effect). Goodbye Vista and hello Ubuntu which will run a bit snappier in its own partition.

---

### Post by SuperSonic4 on 2009-12-24
> **coffeecat said:**
> I presume from that you mean that you did install Ubuntu using Wubi. If so, then sorry, no.

A little explanation. A "conventional" dual boot would have shrunk your Vista NTFS partition to make room to create two partition for Ubuntu. One swap partition and one 'root' partition formatted with the Linux filesystem ext4. (NTFS is a Microsoft filesystem.)

Wubi creates a file inside C:\ubuntu (this from memory) in which all the Ubuntu stuff goes. Reformat or delete the C: partition and Ubuntu goes up in a puff of smoke.

You do have one option though. If you really want to be rid of Vista, do a 'proper' install. Boot up from the live CD, start the installer and, at the partitioning stage, choose 'use whole disc' (or words to that effect). Goodbye Vista and hello Ubuntu which will run a bit snappier in its own partition.

Indeed it will, you [the OP] can also specify a separate /home partition (/home/user is where user files go) - this makes upgrades and fresh installs easier IMO. 

Don't forget to back up your files as when you install ubuntu your files will also go poof. External storage such as a USB HDD or flash pen or SD card is best but dropbox or ubuntu one will do

---

