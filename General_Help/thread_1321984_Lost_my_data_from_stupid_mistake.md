---
title: "Lost my data from stupid mistake"
date: 2009-11-10
forum: General Help
---

### Post by 2LSS on 2009-11-10
Ok here is the story. I have a 500gb western digital usb hdd (formatted ntfs3.1) that I use to store .iso 's on. Normally if I want to watch a movie I will use Gmount-iso to mount the iso and then watch it with vlc. The other day I watched a movie and for some stupid unknown reason I pulled my usb hdd cable out with the movie still mounted under gmount and the usb drive still mounted in ubuntu.:mad:
Realizing I made an error, I plugged the drive back in, checked, and my movie directory was gone! I tried unmounting/mounting the drive a few times and restarting the computer. Then I tried ls -a -l in the terminal and got the following: (the dir name is ISOS)
```
d????????? ? ?    ?          ?                ? ISOS
```
I then tried to cd into the directory and got the following:
```
ls: cannot access ISOS: Input/output error
```
I tried using Foremost and Scalpel but they don't support .iso
Are my iso's gone? Should I start re-ripping everything now or is there another tool I could use to recover the data?:-( 
Any help would be MUCH appreciated!

---

### Post by kio_http on 2009-11-10
If the data was on ntfs partition. Your best recovering in Windows. There's a program called Handyrecovery that usually works well for recovering data.

---

### Post by chinmaya_n on 2009-11-10
I think [testdisk]("http://en.wikipedia.org/wiki/TestDisk") can do this !! 
[http://ubuntuforums.org/showthread.php?t=387922](http://ubuntuforums.org/showthread.php?t=387922)
try reading this

testdisk can handle ntfs verywell.... although i've nt tried it, I read it some where!

---

