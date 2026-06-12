---
title: "adjust drive spin speed when inserting a dvd video ?"
date: 2012-10-09
forum: General Help
---

### Post by sdowney717 on 2012-10-09
You can manually slow down the disk so it is quiet by terminal command

'eject -x 4' Where the number can be from 4 to 48 or whatever speed your player can spin the disk. This has to be done everytime you insert a disk.

'eject -x 8' is more silent nice when playing disk.
How can the system be set to do this automatically?
Say when opening VLC etc... it slows the drive down.
I dont know if doing this for every insertion of a disk is right. Maybe just do it everytime VLC starts? I am running gnome 3. I tried a command line change.
Run alacarte and modify the property, but seems to not work, VLC will not start

 /usr/bin/vlc %U
is currently in there
but when I put in 
 /usr/bin/vlc %U & eject -x 8
nothing happens

---

### Post by sdowney717 on 2012-10-09
I created an executable file with this one line.

eject -x 8 /dev/sr0

The /dev/name identifies my drive. Strangely in VLC I have to open /dev/dvd2 to get an inserted disk to play.

So I start VLC or Totem, then as the DVD is racing loud with the movie playing, click and run the file. Then the DVD player slows down to wisper quiet.

---

### Post by dcstar on 2012-10-10
> **sdowney717 said:**
> You can manually slow down the disk so it is quiet by terminal command
.........

```
hdparm -E
``` is supposed to control this, have a look at:

[http://ubuntuforums.org/showthread.php?t=16360](http://ubuntuforums.org/showthread.php?t=16360)

---

### Post by sdowney717 on 2012-10-10
I found a gui for this written for kde
Then a link to an rpm which I converted to a deb
Running it gives me an error

kmdr-executor: not found

What else for minimum of running a kde app is needed?

Or anyone have a link to a deb for gnome on this app?

[http://kde-apps.org/content/show.php?content=18057](http://kde-apps.org/content/show.php?content=18057)


> scott@scott-P5QC:~/Downloads$ sudo alien set-cd-rom-speed-1.1.6-1mdv2007.i586.rpm
set-cd-rom-speed_1.1.6-2_i386.deb generated
scott@scott-P5QC:~/Downloads$ dpkg -i set-cd-rom-speed_1.1.6-2_i386.deb
dpkg: error: requested operation requires superuser privilege
scott@scott-P5QC:~/Downloads$ sudo dpkg -i set-cd-rom-speed_1.1.6-2_i386.deb
dpkg: error: dpkg status database is locked by another process
scott@scott-P5QC:~/Downloads$ sudo dpkg -i set-cd-rom-speed_1.1.6-2_i386.deb
Selecting previously unselected package set-cd-rom-speed.
(Reading database ... 582903 files and directories currently installed.)
Unpacking set-cd-rom-speed (from set-cd-rom-speed_1.1.6-2_i386.deb) ...
Setting up set-cd-rom-speed (1.1.6-2) ...
scott@scott-P5QC:~/Downloads$ set-cd-rom-speed
/usr/bin/set-cd-rom-speed: 2: /usr/bin/set-cd-rom-speed: kmdr-executor: not found
scott@scott-P5QC:~/Downloads$ 


---

