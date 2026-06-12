---
title: "How to autostart a drive?"
date: 2010-07-28
forum: General Help
---

### Post by RapboY on 2010-07-28
My Ubuntu is the latest, Ubuntu 10.04 64-bit.

I have 2 hard drives, one holds windows (160gb), another has three partitions, 15gb for ubuntu 10.04, 5gb for swap, and the remaining 480gb formatted as ntfs for files.. 

The 480gb space is drive D:, my files are located there and i point the apps to get their files from drive D:. For example, "My Music" folder is in drive D:, and so I tell SongBird to grab the music files from that directory. 

It's not a big problem, but whenever I restart ubuntu, drive D: does not automatically open so SongBird initially cannot locate the files. What I want to happen is that when ubuntu starts, drive D: is already loaded, so that the applications can grab the files they need from that drive automatically without me having to manually open drive D: everytime ubuntu starts.

And guys I'm a linux/ ubuntu noob so please don't be hard on me, thank you! :)

---

### Post by aeiah on 2010-07-28
you aren't looking to start or autostart the drive, you're looking to mount or automount it. that might be why your searches arent yielding good results.

you'll have to edit the /etc/fstab file. this is read at startup and contains information about partitions and where to mount them. have a look at a guide that's specifically for mounting ntfs partitions using fstab.


as a side note, when you've accomplished this, you can mount specific folders within your ntfs partition to anywhere within the linux filesystem. ie, you could mount your music folder to the music folder in your home dir, and the same with documents and photos. it isnt necessary, but you may find it useful. this is done with mount --bind.

---

### Post by sXeChris on 2010-07-28
Please reply back if you were able to automount it.

---

### Post by Morbius1 on 2010-07-28
You will need to add a line in fstab that will automount your partition:

STEP 1: Find out how your system sees that partition:
```
sudo blkid -c /dev/null
```It will give you an output that among other things looks something like this:
> [COLOR=Blue]/dev/sda1[/COLOR]: LABEL="WinXP" UUID="DA9056C19056A3B3" TYPE="ntfs" So if you wanted to mount that partition to say /media/Windows:

Open a Terminal and create a mount point:
```
sudo mkdir [COLOR=DarkGreen]/media/Windows[/COLOR]
```Open fstab as root:
```
gksu gedit /etc/fstab
```Add a line to fstab:
> [COLOR=Blue]/dev/sda1[/COLOR] [COLOR=DarkGreen]/media/Windows[/COLOR] ntfs defaults,nls=utf8,umask=000 0 0 Save fstab, exit gedit, and back in the terminal type:
```
sudo mount -a
```You'll know immediately and without rebooting if it works.

---

### Post by RapboY on 2010-07-28
**@aeiah:**
thank you for pointing that out.. sadly, i dont have all the time in the world right now so i cant look them up.. as i said it's not a big problem, maybe i'll give it a shot next time.. (or maybe Morbius1's patience is Godlike and I fix this today with this thread :) )[B] 

@Morbius1:[/B]
thank you for posting that.. not to nitpick, (im the one asking for help here), but i wasnt able to get past Step 1. This was the line that got me confused: 

> So if you wanted to mount that partition to say /media/Windows:did you mean to say "mount that partition to, say, /media.."? i think you did, but I cant understand the logic after that.. so ok, i create a directory (and it would be better if you can try to fit it into my descrription of my system, im sorry i know your trying to help, im a noob sorry).. and then i guess fstab is a text file since i have to open it with gedit.. what does this mean:

> [COLOR=Blue]/dev/sda1[/COLOR] [COLOR=DarkGreen]/media/Windows[/COLOR] ntfs defaults,nls=utf8,umask=000 0 0                      does /dev/sda1 go inside /media/Windows or the other way around? 

and also the last line, would i know it works even if the drive has already previously been mounted?

sorry for all the questions.. im in no hurry to fix this so if you get tired of my questions its ok, thank you again :)

**@sXeChris:**
i did not get past Morbius's step 1.. :(


EDIT: also, i tried running computer janitor, and it erased adobe air, songbird, and twhirl (adobe air app).. i thought all it does is erase the files i used to install the said apps.. is that normal? it really erases the apps themselves?

---

### Post by corncob on 2010-07-28
I've been using "Storage Device Manager" -- "pysdm" in System>Administration>Synaptic Package Manager or
```
sudo apt-get install pysdm
```
It edits fstab for you.
Also, there's "MountManager" in Ubuntu Software Center>System that would appear to do the same thing.

---

### Post by RapboY on 2010-07-28
i tried pysdm but it wont let me use it through my regular user log-on..

i tried mountmanager and there are too many options, im gonna play safe for now and just mount it manually everytime i boot.. only takes 3 seconds anyway..

thanks for those anyway corncob! :)

---

### Post by Morbius1 on 2010-07-28
If you've already created /media/Windows and if in fact blkid says that the partition you want to mount is at /dev/sda1 then the following line:
```
[COLOR=Blue]/dev/sda1[/COLOR] [COLOR=DarkGreen]/media/Windows[/COLOR] ntfs defaults,nls=utf8,umask=000 0 0                      
```Goes at the end of /etc/fstab.

---

### Post by RapboY on 2010-07-28
oh wait what is the "/media/Windows" directory? it's confusing me sorry.. 

the partition i want to mount is named "Jerome" I want to mount that whole partition, it's in /dev/sdb3.. 

so should i put this:

[COLOR=Blue]/dev/sda1[/COLOR] [COLOR=DarkGreen]/Jerome[/COLOR] ntfs defaults,nls=utf8,umask=000 0 0
?

---

### Post by Morbius1 on 2010-07-28
Nope,

I'm betting your partition is not named jerome either. 

I'm beginning to think that the wise thing to do is this:
> im gonna play safe for now and just mount it manually everytime i boot.. only takes 3 seconds anyway..If you want to persue this however please post the output of the following commands:
```
sudo blkid -c /dev/null
``````
ls -al /media
```

---

### Post by RapboY on 2010-07-28
for 

> sudo blkid -c /dev/null
/dev/sda1: LABEL="System Reserved" UUID="2EBCC893BCC856CD" TYPE="ntfs" 
/dev/sda2: UUID="DEAACABDAACA9207" TYPE="ntfs" 
/dev/sdb1: UUID="4aaf6394-7426-4e60-afd1-c75d048dcc4e" TYPE="ext4" 
/dev/sdb3: LABEL="Jerome" UUID="8C26F15226F13E30" TYPE="ntfs" 
/dev/sdb5: UUID="b654ff00-7664-4a29-b453-868040a5474b" TYPE="swap" 

is the UUID the actual name?

for 

> ls -al /media
total 16
drwxr-xr-x  4 root   root   4096 2010-07-28 10:54 .
drwxr-xr-x 23 root   root   4096 2010-07-28 23:16 ..
drwx------  2 root   root   4096 2010-07-26 14:42 HP Personal Media Drive
drwx------  1 jerome jerome 4096 2010-07-27 21:58 Jerome

---

### Post by Morbius1 on 2010-07-28
Son of a gun , it is named jerome:
>  /dev/sdb3: LABEL="Jerome" UUID="8C26F15226F13E30" TYPE="ntfs" _1st: Unmount jerome:_
```
sudo umount /media/Jerome
```_2nd: Create a permanent mount point for jerome to live in:_
```
sudo mkdir /media/Jerome
```_3rd: Open fstab as root:_
```
gksu gedit /etc/fstab
```_4th: Add the following line to the end of the fstab file:_
```
/dev/sdb3 /media/Jerome ntfs defaults,nls=utf8,umask=000 0 0
```_5th: Mount the new fstab entry:_

Save the edited fstab ,
exit gedit,
and back in the terminal type:
```
sudo mount -a
```

---

### Post by RapboY on 2010-07-28
lol yeah i renamed it while creating the partitions i think? anyway, thank you so much for your time and patience! :D

EDIT: oh, and it worked! EDIT: and also, i didnt know it worked after the "sudo mount -a", had to restart or maybe log-off before i find out :)

---

