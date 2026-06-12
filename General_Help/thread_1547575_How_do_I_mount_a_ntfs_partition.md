---
title: "How do I mount a ntfs partition?"
date: 2010-08-06
forum: General Help
---

### Post by fterh on 2010-08-06
I tried ```
sudo mount /dev/sda2
``` but it doesn't work. i tried ```
sudo mount device /dev/sda2
```, nope. what are the commands?

---

### Post by darolu on 2010-08-06
You need to specify a mount point and probably passing some extra options will help (like specifying the type of partition); try:
```
sudo mount -t ntfs /dev/sda2 /mnt
```
It will be mounted at /mnt; I recommend creating a mount point for the partition within /media so it's listed under places and in the left panel of Nautilus:
```
sudo mkdir /media/<yourdisk>
```
Of course you will need to change <yourdisk> to whatever you want.
```
sudo mount -t ntfs -o defaults /dev/sda2 /media/<yourdisk>
```

More info at:
[http://linux.die.net/man/8/mount](http://linux.die.net/man/8/mount)

Another option is to [edit your fstab file]("http://ubuntuforums.org/showthread.php?t=1546744") so the partition gets mounted automatically at start up.

---

### Post by fterh on 2010-08-06
What does /media/ does? Oh got it.

---

### Post by darolu on 2010-08-06
/media is a directory (folder in a graphical file manager).
```
sudo mkdir /media/MyDisk
```
This command will create a directory named "MyDisk" under "/media". /media is the directory Ubuntu uses to mount filesystems by default, so I recommend using it for your mount points.

The mount syntax is: **mount *[COLOR="DarkGreen"]<options>[/COLOR] [COLOR="DarkRed"]<device>[/COLOR] [COLOR="Navy"]<dir>[/COLOR]***

**mount** calls the mount program.
**[color="DarkGreen"]<options>[/color]** this part is optional, this is where you pass the desired options for the mount command, a list of them can be found running "man mount" in a terminal or in the link I posted earlier. The more common options are *-t* (*type* of your filesystem) and of course *-o* (options).
**[color="DarkRed"]<device>[/color]** the device you want to mount, i.e. /dev/sda2, /dev/sdb, UUID=23458910A8, etc...
**[color="Navy"]<dir>[/color]** the directory you want to use as mount point; this is the route where your filesystem will be mounted at.

To see the existing directories in /media type this in a terminal:
```
ls /media
```
And to check what devices are mounted simply run:
```
mount
```

---

### Post by Bucky Ball on 2010-08-06
... or you could just install ntfs-3g and ntfs-config from Synaptics, go to 'System->Admin->NTFS Configuration Tool' and run it and select the ntfs partitions you want mounted. This will re-write fstab to include the partition and mount it at boot. That simple. It will also deal with external NTFS partitions. ;)

---

### Post by fterh on 2010-08-07
I tried ```
sudo mount -t ntfs /dev/sdb3 /media/Windows 7
``` but it didn't work. Any ideas why? And since the device is unique why is there a need for options?

And lastly, my Firefoxes on Ubuntu & Windows 7 share a same profile, so I tried editing the launch command of my Firefox to ```
sudo mount -t ntfs /dev/sdb3 /media/Windows 7; firefox %u
``` but it doesn't work. The semi-colon was for fun I didn't know how it works in Ubuntu.

---

### Post by Elfy on 2010-08-07
Did you make the directory first? If you did and used a space (not a good idea if you can help it) then try
```

sudo mount -t ntfs /dev/sdb3 /media/Windows\7
```

spaces have to be escaped - I think that's the way to do it.

To share your windows profile [http://ubuntuforums.org/showthread.php?t=1138477](http://ubuntuforums.org/showthread.php?t=1138477)

---

### Post by darolu on 2010-08-07
forestpiskie is absolutely right, when you want to include spaces or certain characters (like an &) you need to use "\":
```
sudo mkdir /media/Windows\<space>7
```
Here is a good tip for people who's starting to use the terminal: **TAB key is your friend**, it will auto-complete your commands and routes (well if you're using bash, which is the default), so when you are typing your mount point directory hit the TAB key so it auto-completes it for you; saves time and the risk of a typo is minimal this way.

---

### Post by Elfy on 2010-08-07
> **darolu said:**
> forestpiskie is absolutely right, when you want to include spaces or certain characters (like an &) you need to use "\":
```
sudo mkdir /media/Windows\<space>7
```
Here is a good tip for people who's starting to use the terminal: **TAB key is your friend**, it will auto-complete your commands and routes (well if you're using bash, which is the default), so when you are typing your mount point directory hit the TAB key so it auto-completes it for you; saves time and the risk of a typo is minimal this way.

Excellent point - I love the tab :)

and thanks - I had not had any tea yet when I posted :lol:

---

### Post by fterh on 2010-08-07
I see thanks, my mistake - I didn't create the directory in the first place.

And I actually followed the Lifehacker article on sharing Firefox profiles across OSes, but the problem is I have to mount my Windows 7 partition before I can run Firefox, so is there a way to edit the command of the launcher to mount it?

---

### Post by dino99 on 2010-08-07
as im quite a lazy user, ill prefer to use an easy tool to deal will partitions and devices: mountmanager, set your prefs into: system admin mountmanager

ntfsprogs need to be installed

---

### Post by Bucky Ball on 2010-08-07
+1. I am quite capable of setting up a mount point and doing all this through the terminal but why when you have ntfs-3g??? Having said that, learning the terminal is, of course, an admirable pursuit and good luck with it! ;)

---

