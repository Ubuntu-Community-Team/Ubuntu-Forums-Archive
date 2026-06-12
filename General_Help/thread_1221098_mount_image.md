---
title: "mount image"
date: 2009-07-23
forum: General Help
---

### Post by electrovalent on 2009-07-23
Hello,i am new to linux.I use kubuntu and i want to make a image drive to mount image files.I start making the directory first by typing

john@john-laptop:~$ mkdir ~/Root/media/cdrom1

and i get

mkdir: cannot create directory `/home/john/Root/media/cdrom1': No such file or directory

doing something wrong?

---

### Post by NightwishFan on 2009-07-23
Try this:

```
sudo mkdir /media/virtual
```

Then mount to it using gmountiso or this command:

```
sudo mount -o loop -t iso9660 /path/to/image.iso /media/virtual
```

Make sure to manually unmount the image before mounting another:

```
sudo umount /media/virtual
```

Make sure you remember it is 'u'mount not 'un'mount

Good luck and please ask if you need any help.

---

### Post by jerome1232 on 2009-07-23
> **electrovalent said:**
> Hello,i am new to linux.I use kubuntu and i want to make a image drive to mount image files.I start making the directory first by typing

john@john-laptop:~$ mkdir ~/Root/media/cdrom1

and i get

mkdir: cannot create directory `/home/john/Root/media/cdrom1': No such file or directory

doing something wrong?

Usually things are mounted to /media but if you have your heart set on that location try:

```
mkdir -p ~/Root/media/cdrom1
```

---

### Post by electrovalent on 2009-07-23
it works!thank you!it is dificult to learn all linux commands without asking some times...:D

---

### Post by NightwishFan on 2009-07-23
Two helpful commands to get you started:

```
apropos *searchterm*
```
This will look for commands related to 'searchterm'

```
man *commandname*
```
This will bring up a help file for any particular command.

---

### Post by electrovalent on 2009-07-23
sudo mount -o loop -t iso9660 /home/Music/Solar_Fields_-_Movements-2009-gEm/01-solar_fields_-_movements-gem.cue/media/virtual        
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

---

### Post by electrovalent on 2009-07-23
whith a .cue file i get the above.

---

### Post by jerome1232 on 2009-07-23
2 things.

You forgot a space between .cue and /media

sudo mount -o loop -t iso9660 /home/Music/Solar_Fields_-_Movements-2009-gEm/01-solar_fields_-_movements-gem.cue /media/virtual 


2nd thing, You can't mount .cue files, if you have a .cue file you should also have a .bin file, you need to use the program binchunker to convert them into a .iso

The usage of binchunker is like this

```
bchunk /path/to/.bin /path/to/.cue file.iso
```

Then you would mount the resulting iso file

---

### Post by electrovalent on 2009-07-23
any help?I also try the mkdir -p ~/Root/media/cdrom1 command and nothing happen.no cdrom1 exists inside /media

---

### Post by electrovalent on 2009-07-23
i dont have a .bin file

---

### Post by jerome1232 on 2009-07-23
Well .cue files aren't images, they just describe information about the image file.

You need to get the actual image file (.bin)

---

### Post by DeMus on 2009-07-23
> **electrovalent said:**
> Hello,i am new to linux.I use kubuntu and i want to make a image drive to mount image files.I start making the directory first by typing

john@john-laptop:~$ mkdir ~/Root/media/cdrom1

and i get

mkdir: cannot create directory `/home/john/Root/media/cdrom1': No such file or directory

doing something wrong?

In the folder:
/home/username/.gnome2/nautilus-scripts I have the two scripts which you see as attachments.
Place them on your disk in the right folder. Maybe you have to create it first.
Whenever you right-click on a file you get an item called scripts in the menu, click it and choose either mount or unmount.

---

### Post by electrovalent on 2009-07-23
i will try that thank you all:)

---

### Post by electrovalent on 2009-07-27
nothing seems to work...
Why are so many different ways for doing a simple thing and no one is working?

---

