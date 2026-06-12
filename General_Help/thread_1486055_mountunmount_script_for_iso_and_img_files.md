---
title: "mount/unmount script for iso and img files"
date: 2010-05-17
forum: General Help
---

### Post by SpinningAround on 2010-05-17
I created a script that is able to mount .iso and .img files, it also unmount if used on a already mounted file. I know there is a script to mount .iso files but I haven't found any script that can mount both .iso and .img files. Simply save it in ~/.gnome2/nautilus-scripts/ and make the file executable.

[PHP]
#!/bin/bash
#
# nautilus-file-mounter

gksudo -u root -k /bin/echo "Enter your password for root terminal access"

# Determine if file is ISO,IMG (UDF) or neither
TYPE="$(file -b "$*" | cut -c 3-5)"
if [ $TYPE = 'ISO' ]
	then
	BASENAME=`basename $* .iso`
elif [ $TYPE = 'UDF' ]
	then
	BASENAME=`basename $* .img`
else
	zenity --error --title "File Mounter" --text "File not recognized!"
	exit 1
fi
#Check if the intended mount point already exist,
#in that case ask if the user wish to unmount this AND remove the map
if [ -d /media/"$BASENAME" ] 
then
	#Confirm to unmount
	if zenity --question --title "File Mounter" --text "Unmount $BASENAME at /media/$BASENAME?"
	then
		if sudo umount /media/$BASENAME
		then
			zenity --info --text "Successfully unmounted /media/$BASENAME"
			sudo rmdir "/media/$BASENAME"
			exit 0
		else
			zenity --error --text "Failed to unmount /media/$BASENAME"
			exit 1
		fi
	else
		exit 1
	fi
#Try to mount
else
	#ISO
	if [ $TYPE = 'ISO' ]
	then
		sudo mkdir "/media/$BASENAME"
		if sudo mount -o loop -t iso9660 $* /media/"$BASENAME"
			then
			zenity --info --title "File Mounter" --text "$BASENAME.iso Successfully Mounted."
			exit 0
		else
			sudo rmdir "/media/$BASENAME"
			zenity --error --title "File Mounter" --text "Cannot mount $BASENAME.iso!"
			exit 1
		fi
	#UDF IMG
	else
		sudo mkdir "/media/$BASENAME"
		if sudo mount -t udf -o loop $* "/media/$BASENAME" 
		then
			zenity --info --title "File Mounter" --text "$BASENAME.img Successfully Mounted."
			exit 0
		else
			sudo rmdir "/media/$BASENAME"
			zenity --error --title "File Mounter" --text "Cannot mount $BASENAME.img!"
			exit 1
		fi
	fi
fi
[/PHP]

Sources:
[http://ubuntuforums.org/showpost.php?p=854720&postcount=2](http://ubuntuforums.org/showpost.php?p=854720&postcount=2)
[http://www.ubuntugeek.com/mount-isos-easely-in-gnome-nautilus.html](http://www.ubuntugeek.com/mount-isos-easely-in-gnome-nautilus.html)
[http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html](http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html)
[http://ubuntuforums.org/showthread.php?t=87369](http://ubuntuforums.org/showthread.php?t=87369)
[http://ubuntuforums.org/showthread.php?t=1483438](http://ubuntuforums.org/showthread.php?t=1483438)

---

### Post by SpinningAround on 2010-05-17
I created a script that it able to mount .iso or .img files it's also able to unmount files that it already mounted. Simply select the script on an already mounted image in the nautilus script menu. This script don't required any extra packages except those that come with a standard ubuntu installation.

Follow these steps
```
Save script in a text file and save it as 'mount-unmount.sh' in home directory
```

Following commands in terminal
```
sudo chmod 700 mount-unmount.sh
```

```
mv mount-unmount.sh .gnome2/nautilus-scripts/
```

and you are set, right click on .img or .iso file and use the script.

mount-unmount.sh
[PHP]
#!/bin/bash
#
# nautilus-file-mounter

gksudo -u root -k /bin/echo "Enter your password for root terminal access"

# Determine if file is ISO,IMG (UDF) or neither
TYPE="$(file -b "$*" | cut -c 3-5)"
if [ $TYPE = 'ISO' ]
	then
	BASENAME=`basename $* .iso`
elif [ $TYPE = 'UDF' ]
	then
	BASENAME=`basename $* .img`
else
	zenity --error --title "File Mounter" --text "File not recognized!"
	exit 1
fi
#Check if the intended mount point already exist,
#in that case ask if the user wish to unmount this AND remove the map
if [ -d /media/"$BASENAME" ] 
then
	#Confirm to unmount
	if zenity --question --title "File Mounter" --text "Unmount $BASENAME at /media/$BASENAME?"
	then
		if sudo umount /media/$BASENAME
		then
			zenity --info --text "Successfully unmounted /media/$BASENAME"
			sudo rmdir "/media/$BASENAME"
			exit 0
		else
			zenity --error --text "Failed to unmount /media/$BASENAME"
			exit 1
		fi
	else
		exit 1
	fi
#Try to mount
else
	#ISO
	if [ $TYPE = 'ISO' ]
	then
		sudo mkdir "/media/$BASENAME"
		if sudo mount -o loop -t iso9660 $* /media/"$BASENAME"
			then
			zenity --info --title "File Mounter" --text "$BASENAME.iso Successfully Mounted."
			exit 0
		else
			sudo rmdir "/media/$BASENAME"
			zenity --error --title "File Mounter" --text "Cannot mount $BASENAME.iso!"
			exit 1
		fi
	#UDF IMG
	else
		sudo mkdir "/media/$BASENAME"
		if sudo mount -t udf -o loop $* "/media/$BASENAME" 
		then
			zenity --info --title "File Mounter" --text "$BASENAME.img Successfully Mounted."
			exit 0
		else
			sudo rmdir "/media/$BASENAME"
			zenity --error --title "File Mounter" --text "Cannot mount $BASENAME.img!"
			exit 1
		fi
	fi
fi
[/PHP]

Sources:
[http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html](http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html)
[http://ubuntuforums.org/showthread.php?t=87369](http://ubuntuforums.org/showthread.php?t=87369)
[http://ubuntuforums.org/showthread.php?t=1483438](http://ubuntuforums.org/showthread.php?t=1483438)
[http://www.ubuntugeek.com/mount-isos-easely-in-gnome-nautilus.html](http://www.ubuntugeek.com/mount-isos-easely-in-gnome-nautilus.html)
[http://ubuntuforums.org/showpost.php?p=854720&postcount=2](http://ubuntuforums.org/showpost.php?p=854720&postcount=2)

---

### Post by K.Mandla on 2010-05-20
Moved to General Help. Similar threads merged.

---

### Post by baddnady23 on 2010-10-14
This is a great script, is it possible for someone to modify is so that it will take the selected .iso and unmount it?

---

### Post by megalodon16 on 2010-10-21
Hi guys,
I have a problem...I can't find a good program to mount a CD. 
I want to install a language learner program (rosetta stone) and after i install it with Wine, i have to run it and add a language. The language is an .iso file located on my computer which i cannot browse after it. It simply says: insert the CD with the selected language. I tried to mount with different terminal commands like sudo mount ..., i tried more than 10 programs like gmountiso etc, I even tried nautilus [http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html](http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html) but i couldn;t get to an end, and the application doesn't seem to see the "virtual CD". I tried the same installer in windows, just to make sure everything is ok, and it worked great: after mounting with deamon tools, it recognised immediately the CD.
The problem is that i am running linux on a netbook, so i don't even have a CD-rom :)), so this makes things easier for people who wanted to tell me: burn a cd. :). 

Is there a newbie tutorial about a program/script or something? thank you very much! And for those who will tell me to read the forum before posting/ google the internet and so on, please trust me when I say that I have tried more than 20 ways in making this work during the last 5 days. I must add that i have ubuntu 10.10. Thx

---

### Post by Romanovzky on 2011-08-12
First of all sorry for digging up an old thread but I need help here.

Since the sudo changed versions to 1.7.4-x the time ticket for the gksudo has been change (I've read this somewhere but I'm not a good bash scripter) and so the scripts presented in this thread don't work anymore. Does anyone been able to workaround?

---

### Post by steveray100 on 2012-07-13
Can this script be modified to mount the iso directly without asking for root password?

---

