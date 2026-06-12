---
title: "How to mount ISO using terminal"
date: 2012-04-21
forum: General Help
---

### Post by DeathByLinux on 2012-04-21
Hello,
      I made a post a few days ago trying to figure out how to use Gmount and other applications to mount ISO files, but it got no responses, so I was wondering if you guys could just tell me how to use terminal to mount an ISO file so that the computer sees it as a CD. My CD rom is broken, so I had to convert my old games CDs into ISO files and I plan to use wine to run them. 
-DeathByLinux

---

### Post by Hendronicus on 2012-04-21
> **DeathByLinux said:**
> Hello,
      I made a post a few days ago trying to figure out how to use Gmount and other applications to mount ISO files, but it got no responses, so I was wondering if you guys could just tell me how to use terminal to mount an ISO file so that the computer sees it as a CD. My CD rom is broken, so I had to convert my old games CDs into ISO files and I plan to use wine to run them. 
-DeathByLinux

If it was me, I would do something along the lines of:

Open a terminal

sudo mkdir /media/whatever

sudo mount -t iso9660 -o loop name_of_iso_to_be_mounted /media/whatever


when you're done with the ISO, you unmount with:

sudo umount /media/whatever

There are apps that can do this for you.

---

### Post by DeathByLinux on 2012-04-21
> **Hendronicus said:**
> If it was me, I would do something along the lines of:

Open a terminal

sudo mkdir /media/whatever

sudo mount -t iso9660 -o loop name_of_iso_to_be_mounted /media/whatever


when you're done with the ISO, you unmount with:

sudo umount /media/whatever

There are apps that can do this for you.

It made the directory successfully and I typed in the following in terminal:
sudo mount -t iso9660 -o loop diablo 2 install disk.iso /media/d2install

This is what the terminal said:

```
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .

```

---

### Post by Hendronicus on 2012-04-21
You have spaces in the name of the ISO file. Either rename the file or use escape characters in your mount statement. I would suggest renaming the file without spaces because it's much easier. You could simply use underscores instead of spaces. Like this: diablo_2_install_disk.iso  

Bear in mind that you will definitely need to use the same dir for all the disks or the installer won't work right. There are many tutorials on the web for installing D2 in WINE.

---

### Post by DeathByLinux on 2012-04-22
> **Hendronicus said:**
> You have spaces in the name of the ISO file. Either rename the file or use escape characters in your mount statement. I would suggest renaming the file without spaces because it's much easier. You could simply use underscores instead of spaces. Like this: diablo_2_install_disk.iso  

Bear in mind that you will definitely need to use the same dir for all the disks or the installer won't work right. There are many tutorials on the web for installing D2 in WINE.
Renamed the ISO to d2install.iso, then typed the following: 
```
sudo mount -t iso9660 -o loop d2install.iso /media/d2install
[sudo] password for usr: 
d2install.iso: No such file or directory
```

---

### Post by Hendronicus on 2012-04-22
Well, I'm only guessing at this point but I would say that you either are not in the right directory with the ISO, mistyped the filename, or mistyped your password.

I've done all of these many times.

---

### Post by DeathByLinux on 2012-04-22
> **Hendronicus said:**
> Well, I'm only guessing at this point but I would say that you either are not in the right directory with the ISO, mistyped the filename, or mistyped your password.

I've done all of these many times.

Haha, sorry to frustrate you, man.

Am I supposed to put the iso file path in the command? 


sudo mount -t iso9660 -o loop d2install.iso /media/d2install

I thought the "/media/d2install" is the place where the iso would be mounted? Is that where I am supposed to put the file path to where the iso is located?

---

### Post by Hendronicus on 2012-04-22
> **DeathByLinux said:**
> Haha, sorry to frustrate you, man.

Am I supposed to put the iso file path in the command? 


sudo mount -t iso9660 -o loop d2install.iso /media/d2install

I thought the "/media/d2install" is the place where the iso would be mounted? Is that where I am supposed to put the file path to where the iso is located?

Yes, that would be a good idea. If you are in the same directory with the ISO you shouldn't need to, but it certainly can't hurt. You're not really frustrating me, so don't worry about it.

---

### Post by Hendronicus on 2012-04-22
Just to be clear:

sudo mount -t iso9660 -o loop /path/to/d2install.iso /media/d2install

---

### Post by DeathByLinux on 2012-04-22
> **Hendronicus said:**
> Just to be clear:

sudo mount -t iso9660 -o loop /path/to/d2install.iso /media/d2install

Okay, that worked, but it seems that I am running into the same problem that I did when I was doing this using other applications like Gmount.
When I go to install it, I type:
```
wine /media/d2install/install.exe
```
It says, "Please insert CD labelled 'Install Disc.'"
Now, I thought that is what I just mounted, so why is it asking me to insert the CD that is already mounted? Does it not detect the fact that it is mounted? This problem also arose when I used Gmount to try and install other games that I made ISOs of. I used to able to install games, but now I can't.
Ideas?

---

### Post by Hendronicus on 2012-04-22
How did you make the ISO? If you didn't use a method that makes true images then most likely it did not copy the hidden, copy-protected tracks of the CD. The installer is probably looking for these. I've run in to that a few times and all I can say is that some programs are better than others at making these kinds of copies. I would get into trouble saying anything else about it on this site.

---

