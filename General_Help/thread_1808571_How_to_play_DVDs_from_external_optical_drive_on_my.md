---
title: "How to play DVDs from external optical drive on my ASUS EEE PC 901?"
date: 2011-07-20
forum: General Help
---

### Post by ra1511 on 2011-07-20
Sorry if this question might sound stupid I'm a complete noob here. I bought an ASUS EEE PC 901 second hand and had reformatted the hard disk with a fresh installation of Ubuntu 10.10 netbook remix. formatted the 2 drives as follows : 4 gb hard disk space ext4 , and 8 GB hard disk space ext4 This was after countless problems with Ubuntu 11.04 Desktop edition previously not being able to connect to the internet via my home wifi router. I took the advice on this forum somewhere, someone said 10.10 NBR will not have issues with wifi connectivity. Tried it and it worked. On my current Ubuntu NBR 10.10 installation, absolutely no wifi connectivity problems whatsoever.

Now my brand new MyLink portable USB Optical Drive which plays DVDs and CDs has arrived in the post. I open it, plug it into my ASUS eee pc 901. And nothing happened. I am used to using Windows and its Plug and Play function. Now for the life of me, this just doesn't happen in Ubuntu right now. The computer does recognise the drive though. Under Applications > Disk Utility I can see the optical drive right there and there's an option to use Brasero to copy and burn DVDs. However no option to play. I tried using the Movieplayer that comes installed with this Ubuntu version to play the DVD I'd insertedd into the drive, but on clicking "Add file" to try and search where on the system the DVD file is located, nothing turns up. All I can see are my home directory and the files on my hard drive.

The external optical drive came with a CD with the drivers on the CD, meant to be installed I think. But I have absolutely no idea how to install it on Ubuntu. Or if I need to install it.

Can anybody help me out please? I'm starting to think maybe I should have just stuck to the Windows XP that came with this netbook. I would prefer to stick with Ubuntu though as its supposedly faster than Windows... 

Rachel

---

### Post by wolfen69 on 2011-07-20
External drives normally don't need drivers to work. Try installing the DVD codecs. In a terminal, do:
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by seawolf167 on 2011-07-20
Have you mounted the drive?

```
man mount
```

or more specifically, plug in your drive, then type

```
sudo lshw -class disk
```

to get your drive's logical name, then make a directory for the drive

```
sudo mkdir /media/cdrom1
```

and mount the drive

```
sudo mount /dev/*sr0* /media/cdrom1
```

where sr0 is your device's name

If mounting works and you can access and use the drive, then we can walk you through adding an /etc/fstab entry to automatically mount the drive at boot

As for playing DVDs, you will need a couple extra packages

```
sudo apt-get install ubuntu-restricted-extras
sudo apt-get install libdvdread4
sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by ra1511 on 2011-07-20
wolfen, i tried the command you suggested in terminal window. got the error message "command not found"

---

### Post by ra1511 on 2011-07-20
seawolf, tried your suggestion. went okay it seems, until when i entered this one : 
sudo mount /dev/*sr0* /media/cdrom1and it gave me an error message "can't find /dev/sr0/media/cdrom1 in /etc/fstab or /etc/mtab"

any more suggestions please???

---

### Post by ra1511 on 2011-07-20
if it helps this was the message which appeared when i typed the sudo lshw command that seawolf suggested :

 *-disk:0                
       description: ATA Disk
       product: ASUS-PHISON SSD
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/sda
       version: TST2
       serial: SOQ1682274
       size: 3847MiB (4034MB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=0003ea59
  *-disk:1
       description: ATA Disk
       product: ASUS-PHISON SSD
       physical id: 0.1.0
       bus info: scsi@1:0.1.0
       logical name: /dev/sdb
       version: TST2
       serial: SOQ1782240
       size: 7695MiB (8069MB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000c8cb5
  *-cdrom
       description: DVD reader
       product: RW/DVD GCC-4240N
       vendor: HL-DT-ST
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 0213
       capabilities: removable audio cd-r cd-rw dvd
       configuration: status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom

---

### Post by seawolf167 on 2011-07-20
Try this command instead

```
mount -t iso9660 /dev/cdrom /media/cdrom1
```

---

### Post by seawolf167 on 2011-07-20
> **ra1511 said:**
> wolfen, i tried the command you suggested in terminal window. got the error message "command not found"

Try trying the bottom 3 commands from my first post - make sure you type them exactly as shown. Tab completion helps.

---

### Post by ra1511 on 2011-07-20
hi seawolf. just tried what you suggested with regards the command mount -t iso9660 /dev/cdrom /media/cdrom1
 got an error message saying "only root can do that". 
what is going on? do i have a defective optical drive ??

---

### Post by seawolf167 on 2011-07-20
Nope - just use a *sudo* in front of the command

```
sudo mount -t iso9660 /dev/cdrom /media/cdrom1
```

---

### Post by ra1511 on 2011-07-20
okay seawolf, did what you said - typed in the last 3 commands you described earlier on, and it took a long time but eventually lots of stuff got installed from the looks of it. then i mounted the cdrom drive with that sudo command, and it seemed to work. now when i go into movieplayer, and click "add" i see that the cdrom drive is now on the list. problem now is i have no idea how to playback the dvd in the drive now... there are two sets of files on the cdrom drive - audio file. and video file. and when i go into each file, there were loads of files. what or which one do i click to playback the dvd??? also another thing is... am i done with all the terminal window work now? i don't need to do all of that again when i power on my computer again will i??? sorry if i'm asking too many questions...

---

### Post by seawolf167 on 2011-07-20
Instead of opening the dvd like a folder, if you right click, select "open with" then use either VLC or MPlayer to run the dvd does it work?

---

### Post by ra1511 on 2011-07-20
i had to install vlc player from ubuntu software center just now. but after installing, i opened the dvd fine. thanks so much seawolf... you're a star! now i just hope i won't have to do all that terminal window stuff again...

---

### Post by seawolf167 on 2011-07-20
> **ra1511 said:**
> now i just hope i won't have to do all that terminal window stuff again...

To avoid this, you'll want to add an entry in /etc/fstab

Fortunately, this isn't too bad

Unmount the device

```
sudo umount /media/cdrom1
```Open /etc/fstab for editing

```
sudo gedit /etc/fstab
```at the bottom, add the line

```
/dev/cdrom    /media/cdrom1   udf,iso9660 ro,user,noauto      0       0
```save the file, exit, restart with it plugged in and see if it automounts

EDIT: edited the /etc/fstab entry

---

### Post by wolfen69 on 2011-07-20
> **ra1511 said:**
> wolfen, i tried the command you suggested in terminal window. got the error message "command not found"

Are you copying and pasting it?

---

### Post by ra1511 on 2011-07-21
seawolf, tried your commands and edited that file by copying and pasting the line you wrote. upon restarting the computer and going into vlc player, the external dvd drive is still not showing. i had to go into terminal window and mount the device again using your command : 
sudo mount -t iso9660 /dev/cdrom /media/cdrom1 
after that when i go into vlc player, external dvd drive shows up in the directories as cdrom1 and i can play it again.

it doesn't seem to be automounting. 

any ideas why?? or what i can do apart from having to mount it everytime i use the drive??

---

### Post by ra1511 on 2011-07-21
wolfen, i didn't copy and paste your command yesterday when i tried. i just typed it in... i don't suppose i typed it in wrong though ... but anyway, today i tried copying and pasting it into the terminal window as you suggested. now i don't get an error message anymore so it worked this time i think. but after that, i went into vlc player and my external dvd drive is still not showing up. i have to go into terminal window and mount that device again before it will show up on the files and directories of vlc player. any ideas why this is happening or what i can do about it??

---

### Post by ra1511 on 2011-07-21
another thing that i noticed was that every time i plugged in the external dvd player into my computer's usb port, the computer just switches off / blacks out. i have to press the power on button on the computer to turn it back on again, and then after it starts up, i realise the dvd player is not recognised in vlc player and have to go to terminal to mount it again before it is recognised. isn't this odd??

---

### Post by seawolf167 on 2011-07-21
> **ra1511 said:**
> seawolf, tried your commands and edited that file by copying and pasting the line you wrote. upon restarting the computer and going into vlc player, the external dvd drive is still not showing. i had to go into terminal window and mount the device again using your command : 
sudo mount -t iso9660 /dev/cdrom /media/cdrom1 
after that when i go into vlc player, external dvd drive shows up in the directories as cdrom1 and i can play it again.

it doesn't seem to be automounting. 

any ideas why?? or what i can do apart from having to mount it everytime i use the drive??

You shouldn't need to since it is a cdrom drive, but try removing the "noauto" option in your /etc/fstab entry and see if that helps.

---

### Post by ra1511 on 2011-07-21
seawolf, did what you said about removing the noauto in the fstab file. it automatically mounts now. thanks.

---

### Post by seawolf167 on 2011-07-21
> **ra1511 said:**
> seawolf, did what you said about removing the noauto in the fstab file. it automatically mounts now. thanks.

Awesome :)

If it is all solved, please mark the thread as such under "Thread Tools"

---

