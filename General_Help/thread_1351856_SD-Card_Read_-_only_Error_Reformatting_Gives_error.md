---
title: "SD-Card Read - only Error Reformatting Gives error"
date: 2009-12-11
forum: General Help
---

### Post by xsinsx on 2009-12-11
Hello, I am curious if anyone could help me with this problem. I recently Purchased a Micro SD card and I put some music on it for my new phone well I go to add some more music to it and it gives me a read only error I have tried sudo and sudo -s 

[I][SIZE="1"]:~/Downloads$ sudo mv The\ Highstreet\ Allstars\ -\ Rock\ That\ Beat.mp3 /media/3016-2C9E/music
mv: inter-device move failed: `The Highstreet Allstars - Rock That Beat.mp3' to `/media/3016-2C9E/music/The Highstreet Allstars - Rock That Beat.mp3'; unable to remove target: Read-only file system[/SIZE][/I]

[I][SIZE="1"]:~/Downloads# mv The\ Highstreet\ Allstars\ -\ Rock\ That\ Beat.mp3 /media/3016-2C9E/music
mv: inter-device move failed: `The Highstreet Allstars - Rock That Beat.mp3' to `/media/3016-2C9E/music/The Highstreet Allstars - Rock That Beat.mp3'; unable to remove target: Read-only file system[/SIZE][/I]

My next step was i tryed a CHMOD of the Files and Whole SD Card and i got this error:

[SIZE="1"][I]:/media/3016-2C9E$ ls
BLUETOOTH  DCIM  EMAIL  Media  MUSIC  RECORD

:/media/3016-2C9E$ chmod 777 MUSIC
chmod: changing permissions of `MUSIC': Read-only file system[/I][/SIZE]

I then proceeded to using Gparted to try and Reformat the whole SD Card and i got an error log file that read: 

[I][SIZE="1"]GParted 0.4.5

Libparted 1.8.8.1.159-1e0e

Delete /dev/mmcblk0p1 (fat16, 1.84 GiB) from /dev/mmcblk0  00:00:01    ( ERROR )
    	
calibrate /dev/mmcblk0p1  00:00:00    ( SUCCESS )
    	
path: /dev/mmcblk0p1
start: 135
end: 3854335
size: 3854201 (1.84 GiB)
delete partition  00:00:01    ( ERROR )
libparted messages    ( INFO )
    	
Unable to open /dev/mmcblk0 read-write (Read-only file system). /dev/mmcblk0 has been opened read-only.
Unable to open /dev/mmcblk0 read-write (Read-only file system). /dev/mmcblk0 has been opened read-only.
Unable to open /dev/mmcblk0 read-write (Read-only file system). /dev/mmcblk0 has been opened read-only.
Unable to open /dev/mmcblk0 read-write (Read-only file system). /dev/mmcblk0 has been opened read-only.
Unable to open /dev/mmcblk0 read-write (Read-only file system). /dev/mmcblk0 has been opened read-only.
Can't write to /dev/mmcblk0, because it is opened read-only.
Unable to open /dev/mmcblk0 read-write (Read-only file system). /dev/mmcblk0 has been opened read-only.[/SIZE][/I]

If anyone could help me I would appreciate it... I've tryed everything I can think of and it just doesnt make sense even after CHMOD 777 the files... that it wont give up the read only status please if any additional information is needed i can get it. Just let me know any ideas guys.

---

### Post by xsinsx on 2009-12-12
Bump

---

### Post by niteshifter on 2009-12-12
Hi,

Are you using the microSD with an SD card adapter so that it fits in the reader slot? If so, there's a tiny switch on the side of the adapter - make sure it is not in the lock position.

---

### Post by xsinsx on 2009-12-12
Gah... that was it... im use to jump drives this is my very first handset... so my first time fiddling with an SD card... yes it is an SD with an adapter... so... yea... thank you that was it... i wish i would have noticed that it was locked earlier... i feel like i tryed all that for nothing...

---

### Post by jacobs444 on 2009-12-12
for future reference you need to type sudo before chmod, glad you got it though, It usually is that lock on the side.

---

### Post by xsinsx on 2009-12-12
Thank you for the tip it was greatly welcomed :D and yes... it was just annoying... thank you though :)

---

### Post by niteshifter on 2009-12-12
Heh. If I had a nickel for every time I've done that to myself since SD's came out ....

... I could buy a Mac ;)

---

### Post by xsinsx on 2009-12-12
well that makes me feel a bit better but dang a mac that would be nice lol oh well i still am enjoying my linux :D i think i like it better then any mac ive ever worked on.

---

