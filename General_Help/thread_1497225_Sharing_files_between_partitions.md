---
title: "Sharing files between partitions"
date: 2010-05-30
forum: General Help
---

### Post by littlboz on 2010-05-30
Is there a way to share files between my partitions, (dual-boot computer) Ubuntu Lucid Lynx and Mac OS X

---

### Post by HermanAB on 2010-05-30
Linux supports the Apple file system, so just mount the Apple partition.

---

### Post by littlboz on 2010-05-30
umm... what do you mean by mount?

---

### Post by Jeroensum on 2010-05-30
Mounting is the act of making an entire filesystem visible in a specified directory (folder).

Fire up a terminal (under the Accessoiries menu) and type in:
sudo fdisk -l (enter your own password when asked) 

You will be presented with a list of partitions, one (or more) of which have an HFS filesystem (Under the System column). Now write down the corresponding Device from the left most column, probably the device will be something like /dev/sda2

Now make a directory in which you want to see your apple filesystem:
mkdir /home/<your username>/apple

Last, try and mount your volume:
  sudo mount <device name here> <mount point here>
which would look like something like this:
  sudo mount /dev/sda2 /home/jeroensum/apple

If your system starts calling you names and dislikes the fact that you are trying to mount an apple partition try to persuade it with the installation of these packages:

sudo aptitude install hfsplus hfsprogs hfsutils

Sometimes adding the filesystem type to the mount command helps:
 mount -t hfs /dev/sda2 /home/jeroensum/apple

---

### Post by littlboz on 2010-05-30
omg omg thank you ^_^.

Just out of curiosity this would work for windows correct? Just that most of the files wouldn't work (I'm using wine however :-D).

I know that apple and linux are very similar would this code also work on the apple partition so I could mount Ubuntu to the Apple?

---

### Post by Jeroensum on 2010-05-30
This should also work for windows partitions, the filetype there should be NTFS or if it's a win95/98 machine it could even be FAT or FAT32. If it's NTFS and your linux box refuses to mount then check if you have the ntfs-3g package(s) from the repo's. However, these should already be present on your box if you have a standard (up2date) desktop. 

The only thing I know about apples is that they taste great, hmm wrong apple eh? j/k Apple OS is a UNIX spinoff so in theory this should work on the apple cli as well. The (linux) filetype you should look for there would be ext3 or ext4, ext2 is often used for the /boot partition and probably won't contain any usefull info.

Btw,
There is even an ext3 driver for windows but in my experience that's a pretty buggy piece of work and I would recommend you stay away from it if you like your files to be intact and your OS to be stable. ;)

Btw2,
Running windows executables in wine is possible but often buggy. Try to obtain alternative software where you can: open office <-> MS office , Gimp <-> Photoshop, etc. For most of the windows software out there there are alternatives :) Most file(s) and fileformats are also supported so there's just a steep learning curve getting to know all the new programs :)

---

### Post by littlboz on 2010-07-31
Okay, I kind of took a break from Ubuntu for a while and now I'm back. There are 2 things that I've noticed. The first is that my apple OS seems to be already mounted to my desktop which I really like. Is this a new feature?

The second thing is when I go to the mounted folder and I click on user<my user name<music I can't open music because the the permission isn't allowing me to do so. I tried right clicking on it and changing the permissions that way but the box was gray and unclickable. I have a feeling I will have to go into my music folder in the apple OS X to change this. Any suggestions?

---

### Post by varunendra on 2010-07-31
If a folder is created in OSX, then it is perhaps better and safer to change its permissions from there.

Otherwise, try opening nautilus (in ubuntu) with root privileges
```
gksudo nautilus
```
and try again.

---

