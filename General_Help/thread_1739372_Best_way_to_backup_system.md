---
title: "Best way to backup system"
date: 2011-04-25
forum: General Help
---

### Post by Wuxin on 2011-04-25
I am using Ubuntu 10.10 on an IBM ThinkPad and I would like to know what the most convenient way is to backup my system hard drive?  I have an external hard drive with a USB connection, but I cannot have it mounted all the time.  I take my laptop with me and it's hardly practical to have an external drive attached at all times.  

Is there a way I can mount the external drive, say, once a day or every other day, and run a backup program manually at that time?  I use SeaMonkey and Firefox as browsers; there is certainly no reason to back them up.  Thank you for your attention!

---

### Post by CharlesA on 2011-04-25
You can write a script to mount the drive and run rsync to back up your home directory.

I use a script daily that does that.

---

### Post by collisionystm on 2011-04-25
Just use Rsync

You can create a desktop launcher to run the command

rsync -aqv /source/* /destination

It does one full backup and the next times you run it, it will only send over changed and updated files.

---

### Post by Wuxin on 2011-04-26
[FONT=Times New Roman][SIZE=3]Thank you for the above.[/SIZE][/FONT]  [FONT=Times New Roman][SIZE=3]Now in the script posted:

[/SIZE][/FONT]rsync -aqv /source/* /destination

[FONT=Times New Roman][SIZE=3]What is it you put in place of "source" and  also "destination"?  My source will 
be my laptop and the  destination will be a usb external drive.  Do those need to be explicated or will the above script take care of that?  Also, how do you create the desktop launcher you mentioned?  Thanks so much--this is very helpful!
[/SIZE][/FONT]

---

### Post by abhilashm86 on 2011-04-26
I use my own script to backup files and home directory, this is piece of code, you can modify to your use. 

I usually have two large USB drives of 320GB, just plug any USB and enter its name and run this program. Do tell me how it goes.......


```
#! /usr/bin/env python
import sys
import os
import tarfile
import datetime

drive = raw_input('enter drive name to make backup ')
 

d = datetime.datetime.now()
dateVar = d.strftime('%Y%m%d_%H%M')

if not os.path.exists('/media/%s/backup' %drive):
 os.mkdir('/media/%s/backup' %drive)


tarFile = tarfile.open("/media/%s/backup/%s.tar.bz2" %(drive, dateVar), 'w:bz2')

#files to be added for tar
try:
    for f in ['/home/abhilash/Programming', '/home/test/misc']:
#If you don't want whole directory structure, then use arcname like following tarFile.add(f, arcname = '%s' %dateVar). Then when you extract, a folder at root level of arcname will be created
        tarFile.add(f)

#show the archived files
    for f in tarFile.getnames():
        print "Added %s" % f
except OSError, why:
    print why

tarFile.close()
```

---

### Post by CharlesA on 2011-04-26
Just wanted to note that I've had problems using /path/to/source/* [COLOR="Blue"]not[/COLOR] copying any hidden files.

Use this instead:

```
/path/to/source/
```

---

### Post by Wuxin on 2011-04-26
[FONT=Times New Roman][SIZE=3]Clearly I'm dealing with some very experienced users here!  I don't know terms like tarFile and have no idea what they refer to.  I just need a basic script for backing up files in case of an emergency.  I understand that "rsync" seems to be the way to go on this but apparently there are numerous possible modifications on it.  Do you have to give your external drive a "name"?  Is that Linux's way of identifying it?

There are some front end packages available for backup like *deja dup*.  Do you advise against using that kind of thing?
[/SIZE][/FONT]

---

### Post by CharlesA on 2011-04-26
Yes. You need the "mount" the external drive somewhere and then tell rsync where the destination is going to be.

There is a frontend called Grsync, which much help, but if you want to have it automated, you'll have to use a shell script (command line/terminal).

---

### Post by collisionystm on 2011-04-26
When your Exernal drive is connected, it will probably be in /media

Open a terminal

type
```

cd /media

```Now to list what you have in this directory, type .....

```

ls              < that is a lowercase LS

```You should see your drive in there.

Since you are always on the move, I suggest only backing up your home directory files.

Right click on your desktop
CREATE LAUNCHER
Name = BACKUP
command = ```
rsync -arv --progress /home/<yourusername>/* /media/<usbdrive>/BACKUP
```Now whenever your drive is connected, just double click on the launcher you made to run the command.

---

### Post by abhilashm86 on 2011-04-27
> **CharlesA said:**
> Yes. You need the "mount" the external drive somewhere and then tell rsync where the destination is going to be.

There is a frontend called Grsync, which much help, but if you want to have it automated, you'll have to use a shell script (command line/terminal).

Thanks for that Grsync, the python script also does the same thing but it tar.gz so filesize will be quite reduced.

---

### Post by abhilashm86 on 2011-04-27
> **Wuxin said:**
> [FONT=Times New Roman][SIZE=3]Clearly I'm dealing with some very experienced users here!  I don't know terms like tarFile and have no idea what they refer to.  I just need a basic script for backing up files in case of an emergency.  I understand that "rsync" seems to be the way to go on this but apparently there are numerous possible modifications on it.  Do you have to give your external drive a "name"?  Is that Linux's way of identifying it?

There are some front end packages available for backup like *deja dup*.  Do you advise against using that kind of thing?
[/SIZE][/FONT]

I thought that you had similar issue of backing system, you just need to insert a USB drive and it'll mount it automatically. Then see the label name of drive and run the program and enter the name of drive(I did not hardcode the name of USB drive in program, since i run this program on multiple devices, but you can mention name in the script itself). 

The advantage of this script is it'll tar.gz the files you are backing up, so filesize is reduced.

---

