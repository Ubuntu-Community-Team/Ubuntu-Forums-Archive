---
title: "Mounting HD partitions automatically"
date: 2006-04-14
forum: General Help
---

### Post by Mishal on 2006-04-14
If I attach a friend's HD to my PC, isn't there a way I can make the partitions of that HD get detected automatically?

I know it works if it's an external HD. But I am talking about an internal HD. It is embarassing in front of my Windows-loving friends to struggle with Linux to get partitions of HD to be made accessible by making folders in /media and then writing code in the terminal etc etc.

Surely there's a shortcut to automounting partitions?:)

---

### Post by Sutekh on 2006-04-14
Edit the /etc/fstab - automounting configuration file, and then you can forget about it.

Good Links

[TuxFiles.org - How to edit and understand the /etc/fstab](http://www.tuxfiles.org/linuxhelp/fstab.html)

[http://psychocats.net/ubuntu/mountwindows.php](http://psychocats.net/ubuntu/mountwindows.php)

---

### Post by aysiu on 2006-04-14
[QUOTE=Mishal]
I know it works if it's an external HD. But I am talking about an internal HD. It is embarassing in front of my Windows-loving friends to struggle with Linux to get partitions of HD to be made accessible by making folders in /media and then writing code in the terminal etc etc.[/QUOTE] If you find that sort of thing embarrassing, don't use Ubuntu. Seriously.

Use Knoppix or Mepis.

---

### Post by Mishal on 2006-04-14
aysiu, cool down mate :)

I presume you have not faced a situation where your friends have come to your house hoping to see something good about the Linux you were talking to them about all day and then they find out that you have to go through a lot of steps just to access the partitions in the file manager. Yes, yes, I know Linux is not Windows and I have read almost all the articles in your website plus that famous long article 'Linux is not Windows'. 

I am not expecting Linux to be like Windows either. But at least, the developers can easily add the feature of automount for any HD being attached to the PC. It's not that big a deal, is it?

---

### Post by aysiu on 2006-04-14
[QUOTE=Mishal]aysiu, cool down mate :)

I presume you have not faced a situation where your friends have come to your house hoping to see something good about the Linux you were talking to them about all day and then they find out that you have to go through a lot of steps just to access the partitions in the file manager. Yes, yes, I know Linux is not Windows and I have read almost all the articles in your website plus that famous long article 'Linux is not Windows'. 

I am not expecting Linux to be like Windows either. But at least, the developers can easily add the feature of automount for any HD being attached to the PC. It's not that big a deal, is it?[/QUOTE] I'm not saying that you're proposing Linux should be like Windows.

I'm just saying that if impressing people with Linux's automating of tasks is a priority, Ubuntu shouldn't be the distro you present them with.

Knoppix is far more impressive in that sense. It has all your partitions and hard drives laid out on your desktop. Once you click on the partition, it automounts and opens.

Ubuntu also doesn't have proprietary codecs by default, so it's not impressive that way to a lot of people who just want to see some video on the internet.

I'm not angry about it. I'm just saying you may want to think about using another distro.

---

### Post by Mishal on 2006-04-14
> I'm just saying that if impressing people with Linux's automating of tasks is a priority, Ubuntu shouldn't be the distro you present them with.
No, that's not my priority but anyway I got your point.

Nevertheless, is there any reason why the mounting system should NOT be automated? I mean to say, let Ubuntu detect the partitions automatically and still allow adanced users to modify the features in fstab if they wish to.

That seems fair enough, doesn't it?

---

### Post by Sutekh on 2006-04-14
[QUOTE=Mishal]No, that's not my priority but anyway I got your point.

Nevertheless, is there any reason why the mounting system should NOT be automated? I mean to say, let Ubuntu detect the partitions automatically and still allow adanced users to modify the features in fstab if they wish to.

That seems fair enough, doesn't it?[/QUOTE]
For me it did.  It put 8 little hard drives on my desktop (one for each partition) as soon as I'd installed Breezy.  This also happened when I installed Dapper aswell.  Was your second HHD in place when you installed?

---

### Post by Mishal on 2006-04-14
Yes, my second HD was in place when I installed ubuntu but I am not having problems with that since I have edited fstab accordinly.

The problem arises whenever someone comes to my house to copy a file from my hard disk and when I attach his hard disk to my PC, it takes 15 minutes just to get the partitions to be accessible on ubuntu. Needless to say, I can of course edit fstab, but I don't feel like doing it every time I have to attach a hard disk for copying a single file.

And finally, if partitions of external HDs can be made accessible automatically, why not internal HDs? Any particular security reasons that I am not aware of?

---

### Post by Bokonon on 2006-04-14
Yes, a simple edit of your fstab file will automount whatever you want and mount it the way you want.  I just did this the last couple of days and searching here you will find easy HOWTOs.  Be sure to backup your fstab file just in case you have trouble.

I have ntfs, ext3, swap and vfat partitions all working just the way I want them to.

For external drives, cds and flash disks, they automout for me just fine.

---

### Post by taurus on 2006-04-14
The bottom line is you need to edit your /etc/fstab if you insert a new harddrive into your machine!!!  Create a mount point and edit /etc/fstab and mount it takes like 30 seconds!!!  Then, I can impress them with Ubuntu the other 14 minutes and 30 seconds...

---

### Post by ubernoob on 2006-04-14
To answer your your questions:

Why isn't internal disks automounted:
because most people that inserts an internal disk does that because they have just bought it and want it mounted in a special way or on a special place. Mine is in /data

External disks are automounted.

You don't need to use fstab. When you insert it, it will do with a single mount command. Which takes 1 second.... not 15 minutes.

sudo mount /dev/hdc1 /media/something

If you want the graphical way to do it, try System --> Administration --> Disks

---

