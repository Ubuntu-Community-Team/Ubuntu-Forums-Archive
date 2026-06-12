---
title: "Partition help"
date: 2010-11-25
forum: General Help
---

### Post by dirtynorth on 2010-11-25
hello all,

I am currently running Windows XP and Ubuntu 10.04 (64 bit) in dual boot on my desktop.  Im wondering if there is a way to set my PC up so that whether I boot into Ubuntu or Windows I will be able to acess all of my files.

My friend seemed to think that there was a way to accomplish this by having multiple partitions.  I currently have two partitions, one for ubuntu and one for XP.

Any help would be appreciated.

---

### Post by Enigmapond on 2010-11-25
I, too, have two partitions. Win7 & Lucid. Ubuntu reads everything but Windoze hate competition and refuses to natively read ext4. The way I had to work around this is to install Ext2Read on the Windoze and now I can, at least, read my other files but in order to access them, I need to copy them and save them on the Win7 partition....I know a pain but this is the only way I found to work around it...

Ext2Read can be found here: [http://sourceforge.net/projects/ext2read/](http://sourceforge.net/projects/ext2read/)

---

### Post by Hippytaff on 2010-11-25
This can be done in a number of ways, one of which is having a seperate partition (ntfs) then bothe win and ubuntu will be able to read and write to it....though an easier way is to allow sharing in your folders in windows and there should be a windows folder in your places menu...you should be able to see them there (I'm a bit rusty on the second option because I don't dual boot any more...others would ahve a better idea about this than me) :-)

---

### Post by sanderd17 on 2010-11-25
it is possible, though not advisable.

You could make a separate /home partition and also use that partition in windows as your user documents. But this is not advisable because:
[list]
[*] ubuntu stores program settings in your home, these would be visible in Windows and make browsing your home folder a real hell
[*] about the partition: ubuntu relies on ext3 or ext4 to save the user rights of the files. Windows doesn't have separate rights for users and can't nativly read ext3 or ext4. If ubuntu doesn't have ext, it will be very fragile. You could also install something to let windows read ext, but I don't know how stable or configurable this is.
[*] if you hibernate windows and reboot it, it will rollback all files changed during this period, this can mean a loss of data. So you'll have to be sure to always completely shutdown windows
[/list]

If you wish to share data, you can make another partition, formatted as NTFS so that windows can read it, and manually put the files you wish to share on the partition.

---

### Post by florus on 2010-11-25
Ubuntu can access all your windows files by mounting your windows partition (found under 'places'). You do not need to 'share' your windows folders for this. Otherwise creating a separate NTFS data partition would do much the same.

---

### Post by coffeecat on 2010-11-25
It's generally not a good idea to write to your Windows C: partition from Ubuntu. Not because NTFS write in Linux is unreliable. It's just that it is just too easy to damage the Windows system accidentally. And, personally, I wouldn't let Windows anywhere near my Linux partition(s) with a third-party ext driver.

I agree with Hippytaff's suggestion to use a separate NTFS data partition for all your shared data. This is what I do on my machines which have both Windows and Linux on them. The partition will be seen as D: or E: or whatever in Windows and will be easily accessible from the Places menu in Ubuntu.

---

### Post by HandyAndy on 2010-11-25
Have you considered a cloud solution such as Dropbox or Box.net? They are both free for a limited amount of storage or you can pay for more.
Your files can be accessed from both OSs and changes made in one are automatically sync'd to the other.

---

### Post by Hippytaff on 2010-11-25
> **HandyAndy said:**
> Have you considered a cloud solution such as Dropbox or Box.net? They are both free for a limited amount of storage or you can pay for more.
Your files can be accessed from both OSs and changes made in one are automatically sync'd to the other.

And ubuntu's very own one of course :-) Called one btw - [https://one.ubuntu.com/](https://one.ubuntu.com/)

---

### Post by dirtynorth on 2010-11-25
Thanks for all the suggestions.  I already have cloud space (dropbox) which I have been using as a work around.  I like he sounds of this separate third partition.  I was planing on ding a fresh install of both OS anyway. 

What would be a good distribution of space between the, I assume three, partitions?

I have a 1.5Tb HD and a Gparted boot disk.

---

### Post by Hippytaff on 2010-11-25
What size HDD do you have?

Edit -> missed the obvious there

others are better placed to assist you with this decission

---

### Post by dirtynorth on 2010-11-25
I guess what I really need to know is how big do the partitions for Ubuntu and XP need to be?  Assuming I can leave the rest as NTFS.

---

### Post by Hippytaff on 2010-11-25
ok...ubuntu doesn't need much more than 10Gb really, without running out of space for installing programs, but a bit more maybe if you want lots of software I'm not sure about windows, I only use it in work :-)

---

