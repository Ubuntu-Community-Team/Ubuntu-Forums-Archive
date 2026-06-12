---
title: "won't recognize usb"
date: 2010-01-31
forum: General Help
---

### Post by imparja2 on 2010-01-31
When everything was working fine, when I inserted the usb or disc an icon would appear asking if I wanted to mount the drive. Now nothing appears. It's been like this almost a year. I haven't used linux since so please explain how to fix step by step. I use hardy heron linux. Can anyone help. Thanx

---

### Post by raktarok on 2010-01-31
Please post the output of following:

```
sudo fdisk -l
```

Then we can manually mount it, if its on the list. 

You don't see any usb icon in the desktop, right?

and may I ask why you waited a year to fix this? :)

---

### Post by imparja2 on 2010-01-31
well I did that and it says invalid option

---

### Post by raktarok on 2010-02-01
> **imparja2 said:**
> well I did that and it says invalid option

That's strange. The command is working fine here. 

Then please post the output of this as soon as you plugin the pen drive.

```
tail /var/log/messages
```

Also try and see the options in Edit >> Preferences >> Media Tab in the file manager, but I am not sure if this will help.

---

### Post by imparja2 on 2010-02-01
ok well I can mount a cd rom. but when I insert the usb nothing appears on the desktop or in my computer. It's the same for every port I have 4 ports

---

### Post by Jotham on 2010-02-01
Is this with every usb?

---

### Post by raktarok on 2010-02-01
Please post the output of the tail command in my earlier post, after you plugin the usb. Its to see if the usb is detected or not.

---

### Post by imparja2 on 2010-02-01
yes it's with all 4 usbs. "Computer" doesn't even register that there is an f drive it just says cd-rw/dvd-rw Drive and Filesystem.

---

### Post by Jotham on 2010-02-01
Sorry I meant usb drive, I wanted to make sure it wasn't a problem with the specific drive.

Does it happen to be a U3 drive?

---

### Post by imparja2 on 2010-02-01
sorry I'm using another laptop to use the internet so I can't post it so I'll send a snap shot it's bad quality though. I can tell you the numbers though if they're too hard to read.

---

### Post by imparja2 on 2010-02-01
what is a u3 drive?

---

### Post by imparja2 on 2010-02-01
here's a better snapshot of the tail command.

---

### Post by raktarok on 2010-02-01
It looks as though the usb drive is not detected at all. Is this the output for only cdrom or did you also plugin the usb drive? The output shows the presence of cd (udf is the filesystem for cd) and did you execute the command immediately after pluggng in the usb? (immediately meaning 5-15 secs) 

Also, as an alternative, if you have gparted partition manager, see if the usb is detected there or not. Find it in the menu or launch it by doing gksudo gparted in the terminal. You will have to look at the right, uppermost corner to change disks.(There will be option like sdb, if the usb is detected) Install gparted if you don't have the program.
```
sudo apt-get install gparted
```

The fdisk command should be working too. Can you do fdisk -v? (It prints the version number)

---

### Post by Jotham on 2010-02-01
It's probably not the cause of your problem, but U3 is a program that comes on some flash drives. I've had problems with them in the past, they seem to emulate a CD drive as well as a flash drive.

---

### Post by imparja2 on 2010-02-01
well it appears the usb is detected look at this. I executed the command like you said this is what happened next

---

### Post by raktarok on 2010-02-01
Ok try this and see if it you get the drive's contents in the file manager:

```
sudo mkdir /media/problematic-usb/
mount /dev/sdb1 /media/problematic-usb/
nautilus /media/problematic-usb/

```

Post any error output that you see.

---

### Post by imparja2 on 2010-02-01
the first command is ok but the second
mount /dev/sbd1 /media/problematic-usb/

then it says "mount: only root can do that"

did I type the command wrong?

---

### Post by raktarok on 2010-02-01
> **imparja2 said:**
> the first command is ok but the second
mount /dev/sbd1 /media/problematic-usb/

then it says "mount: only root can do that"

did I type the command wrong?

Ahh..sorry. My mistake. Add sudo before the whole command. It should read:

sudo mount /dev/sdb1 /media/problematic-usb/

sudo gives you administrative privileges.

---

### Post by imparja2 on 2010-02-01
nautilus /media/problematic-usb opens a file that's empty
ok put sudo in front of it then it says 
"special device /dev/sbd1 does not exist"

---

### Post by raktarok on 2010-02-01
> **imparja2 said:**
> nautilus /media/problematic-usb opens a file that's empty
ok put sudo in front of it then it says 
"special device /dev/sbd1 does not exist"


Please check the spelling - it should be sdb1.(I made the error in my last post, sorry again) If you still get error, post the output of following:

```
ls /dev/sdb*
```

---

### Post by imparja2 on 2010-02-01
I tried all that it says "can't find"

---

### Post by raktarok on 2010-02-01
Can't you use **sudo fdisk -l** ? It would make things much easier.

Also, in the output of this,see if plugdev is listed:
```
groups
```

If plugdev is not listed, do this:
```
sudo usermod -a -G plugdev your_user_name
```

Check if these services are running - if they are not running, replace status by start and plugin the usb.
```
sudo service hal status
sudo service dbus status
sudo service udev status
```

If all this does not yield anything, post the output of this:

```
dmesg | grep usb
sudo blkid

```

Good luck!

---

### Post by lotharmat on 2010-02-01
That's a lowercase L in 

```
sudo fdisk -l
```

---

### Post by imparja2 on 2010-02-01
so to answer your question yes there is plugdev in that list
I got the following outputs for those 3 commands.

---

### Post by raktarok on 2010-02-01
This is weird..

Ok post the output of following after you plugin the usb:

```
cat /proc/scsi/usb-storage/5 
lsusb
ls /dev/sd*
```

If you see sdb in the output of the last command, do this:

```
sudo fdisk /dev/sdb
```

You should be dropped to a fdisk prompt, and from there, press p to view the partition table. Post the result here. You can quit fdisk by pressing q.

and did you try using gparted partition manager and see if the drive is detected there, like I suggested some posts ago? 

Also, do you know the filesystem of the drive? Is it FAT and can you view the usb in other computers? Do other usb drives work fine in your computer?

---

### Post by imparja2 on 2010-02-01
well I did what you said lsusb output was:
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
and ls /dev/sd* had sda, sda1, sda2, sda3. 
There was no "sdb"
I tried searching for gparted partition manager and it could not find
The usb works in the computer I'm using now
but the computer I'm trying to fix has no usb ports work.
What should I do next?
What I mean is I don't think I have gparted partition manager so I can't check if the usb can be detected.

---

### Post by raktarok on 2010-02-01
lsusb should have detected the drive. For example, I get this in my output when I run lsusb with the usb connected.
```
Bus 002 Device 009: ID 0c76:0005 JMTek, LLC. Transcend Flash disk
```

Are you trying to run a usb hard disk? Also, try formatting the usb from a computer where it works. 

For gparted, you can do this, but I don't think gparted will make any difference. Still, you can try..

```
sudo apt-get install gparted
```
```
gksudo gparted
```

Look at the upper right corner. If the usb is detected, there should be an option to change disks.

And do other flash drives work in that computer?

---

### Post by imparja2 on 2010-02-01
well none of that worked I couldn't install gparted either it said the file couldn't be verified but I ignored this and put Y to install but it stayed on 0% completion is it because I'm not connected to the internet. I'm in China so I use a mobile broadband usb and so I can't connect because the computer I'm trying to fix won't detect it. The usb memory stick I'm testing has no problem with it, It works in my other computers.

---

### Post by raktarok on 2010-02-01
I am sorry but I am out of ideas. I don't know what is wrong, maybe other people here in the forum can help you. 

My last suggestions would be these: 

Try formatting the usb drive from your other computers, and see if the usb is now detected by ubuntu.(use fdisk and other commands I posted, then see if there is any change in the output) 

Check if other usb disks work in that computer, maybe all the usb ports are defective? 

You said that you don't have internet connection in that computer, but if you can get a wired connection from somewhere, use it to install all the updates available. Or download the latest ubuntu version and install it - that may fix the problem. You are running hardy heron, right?

Good luck, hope you solve the problem!

---

### Post by rua2 on 2010-05-14
Apologies for reviving an old thread. I just encountered this very problem.

Thanks raktarok, your trick to create a new directory and mount the drive manually worked for me. As did a reboot later :-k

---

