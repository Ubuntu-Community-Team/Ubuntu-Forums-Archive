---
title: "File Menu not visible for all applications"
date: 2010-11-25
forum: General Help
---

### Post by adityachs on 2010-11-25
**Applications working properly with SUDO only :( UBUNTU Noteboox 10.10 XUBUNTU** 			 			 			 		   		 		 		Hi,

I recently installed Ubuntu 10.10 Maverick notebook version on my HP Compaq nc6400
(Intel core2 CPU T5600@1.83GHZ).

Later installed Xfce4. So, I am now on Xubuntu on top of Ubuntu (it seems).

Coming to my problem, even though application working fine normally,  Menu is not displayed in most of the applications. Ex: Transmission,  GIMP, Mousepad, Pinta, gedit ........ No application shows the  file,edit.. menus.

Also file sharing is also not possible in normal mode. When I right click on any folder or file  sharing option is not visible .

[B]But if I run these applications with SUDO the menus are appearing.  When I open nautilus with SUDO , I am able to get sharing options in  right click.

[/B]I tried the below command as advised in[ thread.php?p=6474144]("http://wwww.ubuntuforums.org/showthread.php?p=6474144")
But it failed :sad:
 	PHP Code:
 	[LEFT] 		 			[COLOR=#000000] [COLOR=#0000BB][/COLOR][COLOR=#007700]~$ [/COLOR][COLOR=#0000BB]sudo chown [/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000BB]hR abcd[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#0000BB]abcd [/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]home[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]abcd
chown[/COLOR][COLOR=#007700]: [/COLOR][COLOR=#0000BB]cannot access [/COLOR][COLOR=#007700]`[/COLOR][COLOR=#0000BB]/home/abcd/.gvfs': Permission denied  
[/COLOR] [/COLOR]  		 	[/LEFT]
 
Please advise what to do?

---

### Post by searchfgold6789 on 2010-11-25
Maybe enabling file sharing is just not possible unless you are root :)

As for the other problem, I would try:

[LIST=1]
[*]Boot to any Linux Live CD.
[*]Open up a console/terminal.
[*]Type in the following lines:```
sudo mount /dev/sdXX /mnt
sudo mount --bind /dev  /mnt/dev
sudo mount --bind /dev/pts  /mnt/dev/pts
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys  /mnt/sys
sudo chroot /mnt
```(sdXX is your hard disk)```
[COLOR=Black]sudo chown -hR abcd:abcd /home/abcd
```[/COLOR]
[*]See what happens.
[/LIST]

---

### Post by adityachs on 2010-11-26
> **searchfgold6789 said:**
> Maybe enabling file sharing is just not possible unless you are root :)

As for the other problem, I would try:

[LIST=1]
[*]Boot to any Linux Live CD.
[*]Open up a console/terminal.
[*]Type in the following lines:```
sudo mount /dev/sdXX /mnt
sudo mount --bind /dev  /mnt/dev
sudo mount --bind /dev/pts  /mnt/dev/pts
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys  /mnt/sys
sudo chroot /mnt
```(sdXX is your hard disk)```
[COLOR=Black]sudo chown -hR abcd:abcd /home/abcd[/COLOR]
```
[*]See what happens.
[/LIST]


Sorry I could not understand "Boot any Linux live CD"
You mean to say instead of logging into ubuntu on my hard disk, I need to prepare a linux bootable cd 
like [I]Burning a CD means that you can trial Ubuntu without affecting your  current system. And you can install it alongside or instead of your  system whenever you're ready.
[/I]
Am I correct ?

---

### Post by rupeshsri on 2010-11-26
pleas tell me more about
------------------------------
[URL="http://www.carriersunrise.com"]Re: File Menu not visible for all applications
[/URL]

---

### Post by karthick87 on 2010-11-26
> **adityachs said:**
> Sorry I could not understand "Boot any Linux live CD"



He is telling you to use your ubuntu live cd to boot by changing the first boot device to CD ROM in your BIOS.And then execute his commands in terminal.

---

### Post by adityachs on 2010-12-03
Thanks for trying to help me. When I created new live CD, I was tempted to install fresh to get rid of problems ...so, Now this problem is gone

---

