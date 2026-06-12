---
title: "Disk imaging utility"
date: 2011-03-29
forum: General Help
---

### Post by An Sanct on 2011-03-29
Hello guys!

Well, I know, this question has been asked at least 500 times before, but from all the threads I couldn't get one simple answer...

I'm searching for a GUI disk imager, something, that will be the GUI front end for dd.

PS. Ghost4Linux G4L is not an option, I want to be able to make security backups of my USB thumb drives, CDs, DVDs...

---

### Post by Tmcarr on 2011-03-29
Honestly, DD sounds like the best tool for this job hands down. Is there a specific reason you are looking for a GUI tool? Its pretty simple to:

#dd if=/dev/sd* of=/some/file/here.img

---

### Post by An Sanct on 2011-03-29
I know, dd is powerful and direct, doesn't care about format or size and so on...

All great stuff, but I want to be sure, that after a day of hard work, lets say with my Live USB, that has LAMP and my full php page installed, that I have a backup. And I know, there has to be a GUI tool for this.

PS. GUI is just so, that I don't have to know all the switches and cannot mess up things, I've read about people messing up their entire drives, because of wrong usage of dd.

---

### Post by kiyop on 2011-03-29
You can make GUI tools like:

GUIdd.sh
```
#!/bin/bash
list=$(parted -l|grep -B1 /dev/)
list=$(echo $list|tr " " "_"|sed -e "s/_--_/\n/g"|sed -e "s/^/FALSE /")
list="$list $(blkid|tr " " "_"|sed -e "s/^/FALSE /")"
a=""
while [ -z "$a" ]
do
 a=$(zenity --list --text="Select the device or partition you want to save" --radiolist --column="check" --column="device/partition" $list)
 if [ $? = 1 ];then exit 0;fi
done
a=$(echo $a|sed -e "s/.*\/dev\///"|sed -e "s/:.*//")
b=$(zenity --title="select the directory where the file is saved" --file-selection --directory)
if [ -z "$b" ];then zenity --error --text="Nothing was selected. I will do nothing.";exit 0;fi
c=""
while [ -z "$c" ]
do
 c=$(zenity --entry --text="Type the file name of the saved file" --entry-text="${a}backup$(date -I)"|tr -d " "|tr -d "/")
 if [ -e $b/$c ];then
  zenity --question --text="$b/$c already exists. Do you really want to save to $b/$c ? Saving overwrites $b/$c." --ok-label="Save and Overwrites $b/$c"
  if [ $? = 1 ];then c="";fi
 fi
done
zenity --question --text="Can /dev/$a be saved into the file $b/$c?"
if [ $? = 1 ];then zenity --warning --text="Nothing has been saved.";exit 0;fi
dd if=/dev/$a of=$b/$c
zenity --warning --text="/dev/$a has been saved into the file $b/$c."
exit 0
```It works at least in my Japanese Ubuntu 10.10 by
```
sudo su
bash GUIdd.sh
```

---

### Post by seawolf167 on 2011-03-29
[Clonezilla]("http://www.clonezilla.org")

Then when moving through the prompts, simply use dd as the first priority copying program. Alternatively, you could enter a shell at the beginning and enter your command once you know what it is/how its formatted.

---

### Post by An Sanct on 2011-03-29
Thank you kiyop! I will try that bash script :) (and modify it to my needs,...)

seawolf167:  That looks just like the thing I was looking for, I'll try that too!

I'll tag the thread as solved, once I try clonezilla.

PS. wine + WinImage and other Windows disk imaging software for didn't cut the mustard (at least for me).
PS2. I mentioned winimage, so that others might hit this thread and see the solution...

---

### Post by An Sanct on 2011-03-29
Okay, so I'm disappointed over clonezilla, not because it is bad, but because it is not what I was searching for - a WinImage/WinISO like tool, capable of managing floppy disks, USB flash drives and CD/DVDs.

IMHO, clonezilla is a great tool, but like Ghost4Linux (or Norton Ghost) it requires a special boot or a live version, which is (again) not the GUI I wanted in the first place. It is too much of an "admin with 80 workstations to handle" scenario.

So I'll go with investigating the bash script kiyop posted...

---

### Post by kiyop on 2011-03-30
If you want to manage CD-ROM and/or FDD, you can execute
```
sudo blkid /dev/fd*
sudo blkid /dev/cd*
```though it takes long time maybe because it scans all the cdrom and all the fdd by many possible method.
Especially, /dev/fd0u1440 or so makes the scan long.
So, "fdisk" may be better. "lshw" gives too much information.

And, if an error occurs in "parted" such as read-only error as of CD-ROM, GUIdd.sh script hungs.

The following script is better.

GUIdd.sh
```
#!/bin/bash
list=$(parted -l -s|grep -B1 "/dev/.*:")
list=$(echo $list|tr " " "_"|sed -e "s/_--_/\n/g"|sed -e "s/^/FALSE /")
list="$list $(fdisk -l /dev/cd* 2>/dev/null|grep "/dev/cd.*:"|tr " " "_"|sed -e "s/^/FALSE /")"
list="$list $(fdisk -l  /dev/fd* 2>/dev/null|grep "/dev/fd.*:"|tr " " "_"|sed -e "s/^/FALSE /")"
list="$list $(blkid|tr " " "_"|sed -e "s/^/FALSE /")"
a=""
while [ -z "$a" ]
do
 a=$(zenity --list --text="Select the device or partition you want to save" --radiolist --column="check" --column="device/partition" $list)
 if [ $? = 1 ];then exit 0;fi
done
a=$(echo $a|sed -e "s/.*\/dev\///"|sed -e "s/:.*//")
b=$(zenity --title="select the directory where the file is saved" --file-selection --directory)
if [ -z "$b" ];then zenity --error --text="Nothing was selected. I will do nothing.";exit 0;fi
c=""
while [ -z "$c" ]
do
 c=$(zenity --entry --text="Type the file name of the saved file" --entry-text="${a}backup$(date -I)"|tr -d " "|tr -d "/")
 if [ -e $b/$c ];then
  zenity --question --text="$b/$c already exists. Do you really want to save to $b/$c ? Saving overwrites $b/$c." --ok-label="Save and Overwrites $b/$c"
  if [ $? = 1 ];then c="";fi
 fi
done
zenity --question --text="Can /dev/$a be saved into the file $b/$c?"
if [ $? = 1 ];then zenity --warning --text="Nothing has been saved.";exit 0;fi
dd if=/dev/$a of=$b/$c
zenity --warning --text="/dev/$a has been saved into the file $b/$c."
exit 0
```

---

### Post by Duncan Williams on 2011-03-30
Have a look at the free Easeus programs:
[http://www.easeus.com/download.htm](http://www.easeus.com/download.htm)

They have linux versions of some of there stuff.

or you can create a bootable cd to clone/backup your hard-drive (inc - dual boot)
[http://www.easeus.com/disk-copy/feature.htm](http://www.easeus.com/disk-copy/feature.htm)

If you end up using windows, Have a look at EASEUS TODO.
Free backup/partition/clone > usb etc...

---

### Post by An Sanct on 2011-03-30
> **Duncan Williams said:**
> Have a look at the free Easeus programs:
[http://www.easeus.com/download.htm](http://www.easeus.com/download.htm)

They have linux versions of some of there stuff.

or you can create a bootable cd to clone/backup your hard-drive (inc - dual boot)
[http://www.easeus.com/disk-copy/feature.htm](http://www.easeus.com/disk-copy/feature.htm)

If you end up using windows, Have a look at EASEUS TODO.
Free backup/partition/clone > usb etc...

Thank you, Duncan! I have checked the easeus utility, you recommended. 

I couldn't  believe, the sign, that said "**All** *operating systems*.", so I clicked ... and got a file, that is a "DOS/Windows executable" ... so much for All OSes ... (majorgeeks.com at least says "Win All")

Again, reading through the documentation and comments of that software bundle, I found out, that it creates a bootable CD/USB/ISO, from which you can clone to - or - restore from a file. Its great, its flexible (IE: smaller disks to larger without problems, etc.) and best of all, it is freeware for windows.

So, I am really happy, that you nice people are trying to help, but I am looking for something more like [winimage]("http://www.winimage.com/").

---

### Post by An Sanct on 2011-03-30
Wow, kiyop :) you have shown me something I'm going to love - zenity!

In the past three years I haven't noticed it ... how could I have missed such a cool thing ???

---

### Post by rgb1701 on 2011-03-30
> **An Sanct said:**
> 

So, I am really happy, that you nice people are trying to help, but I am looking for something more like [winimage]("http://www.winimage.com/").

It appears WinIMage works fine under Wine-

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=6903](http://appdb.winehq.org/objectManager.php?sClass=version&iId=6903)

Rated PLatinum, which means it should work "perfectly", more or less ;)

---

### Post by kiyop on 2011-03-30
> **An Sanct said:**
> Wow, kiyop :) you have shown me something I'm going to love - zenity!
Thanks for your reply.:)

You may be able to use WinImage on Wine.

If you want to make backup of a partition and compress the backup (image) and/or restore from the saved backup, you can use "partimage", although I do not know if partimage can deal real CD and/or FDD and/or ext4 partition.
[http://www.partimage.org/forums/viewtopic.php?t=990](http://www.partimage.org/forums/viewtopic.php?t=990)

---

### Post by linis_australis on 2012-03-29
Here is my Disk Image Utility.  It can easily be modified for using ddrescue or gddrescue.  Currenty set up to use fsarchiver

EDIT: now available on sourceforge:  [https://sourceforge.net/projects/linuxdiskimager/](https://sourceforge.net/projects/linuxdiskimager/)

Enjoy  :popcorn:

---

