---
title: "mounting an iso."
date: 2010-11-02
forum: General Help
---

### Post by Blue Summer on 2010-11-02
Hey all, I'm trying to install a game iso I have downloaded. This is a legal game to start with. I can't find ANY instructions on this on the internet. There are so many different ways to mount an iso and I have tried quite a few of them with no success. Apparently there are different types of iso files so how do I find out the type of iso I have so I can look up mounting instructions for it? Thanks guys!

---

### Post by TheAnachron on 2010-11-02
Have you tried mounting it?

Edit: Taken from [MountIso]("https://help.ubuntu.com/community/MountIso").
> sudo mount -o rw,loop example.iso /media/example

---

### Post by Jahid65 on 2010-11-02
Have you used furius ISO Mount?

---

### Post by coffeecat on 2010-11-02
Assuming you're using the gnome version of Ubuntu, have you tried the simplest of all: right-click > Open with Archive Mounter?

---

### Post by Blue Summer on 2010-11-02
Yes to all of them, the open with Archive mounter is empty when it creates it. This is the error from the mount command.

```
rej3kt@Rej3kt:~$ sudo mount -o rw loop sc.iso /media/sc
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
rej3kt@Rej3kt:~$ sudo mount -o rw, loop sc.iso /media/sc
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

### Post by coffeecat on 2010-11-02
The error from the mount command is giving you correct usage help. You made a typo. Compare TheAnachron's code...

> **TheAnachron said:**
> ```
sudo mount -o rw,loop example.iso /media/example                      
```

... with yours....

> **Blue Summer said:**
> ```
sudo mount -o rw loop sc.iso /media/sc
```

Comma, not a space between rw and loop.

---

### Post by Blue Summer on 2010-11-02
Hmm it's giving me an error. 

```
rej3kt@Rej3kt:~$ sudo mount -o rw,loop /Home/Rej3kt/Desktop/sc.iso /media/example
/Home/Rej3kt/Desktop/sc.iso: No such file or directory
```

---

### Post by TheAnachron on 2010-11-02
please note that you have to change /media/example to a folder that is really existing (and empty). 

You can do this before:
sudo mkdir /media/isodir

and then
sudo mount -o rw,loop /Home/Rej3kt/Desktop/sc.iso /media/isodir

---

### Post by matt_symes on 2010-11-02
Hi

Capital H in Home should be small h i.e. /home/...

> rej3kt@Rej3kt:~$ sudo mount -o rw,loop /Home/Rej3kt/Desktop/sc.iso /media/exampleKind regards

---

### Post by Blue Summer on 2010-11-02
Thanks for all the help so far guys. How do I create the mount point because it can't find /media/example :)

---

### Post by matt_symes on 2010-11-02
Hi

sudo mkdir /media/example

Kind regards

---

### Post by Blue Summer on 2010-11-02
Thanks. Now my error is this:

```
rej3kt@Rej3kt:~$ sudo mount -o rw.loop /home/Rej3kt/Desktop/sc.iso /media/example
mount: special device /home/Rej3kt/Desktop/sc.iso does not exist

```

What does it mean "doesn't exist" lol, there's a 7.2gb iso file sat on my desktop called "sc.iso"

---

### Post by matt_symes on 2010-11-02
Hi
[FONT=monospace]
[/FONT]> rej3kt@Rej3kt:~$ sudo mount -o rw.loop /home/Rej3kt/Desktop/sc.iso /media/example

Change 

rw.loop

to 

rw,loop (Notice the comma again)

Kind regards

---

### Post by Blue Summer on 2010-11-02
No idea how that happend!

Same error though

```
 sudo mount -o rw,loop /home/Rej3kt/Desktop/sc.iso /media/example

```

error: ```
/home/Rej3kt/Desktop/sc.iso: No such file or directory

```

---

### Post by matt_symes on 2010-11-02
Hi

Type

ls -al /home/Rej3kt/Desktop/

into a terminal and post back the results.

Kind regards

---

### Post by dtmbmw325i on 2010-11-02
> rej3kt@Rej3kt:~$ sudo mount -o rw,loop /home/Rej3kt/Desktop/sc.iso /media/example Note in this example your username is rej3kt in all lowercase letters, make sure you are typing it the same in your home folder section of that command.  Linux is case-sensitive so make sure any folders or file names you are typing match what they really are.  Windows was not like this, if you are a recent switch.  I hope this helps.  Also make sure there is a comma between rw and loop, and make sure the destination folder is created before you try to mount the iso there.  Hope this helps.

Should look like this most likely:

rej3kt@Rej3kt:~$ sudo mount -o rw,loop /home/rej3kt/Desktop/sc.iso /media/example

---

### Post by dr_duck on 2010-11-02
Why mount rw?  iso's are readonly afaik
```
mount -o loop /pathto/file.iso /pathto/mountpoint
```

---

### Post by Blue Summer on 2010-11-02
Got it mounted thanks!

Matt - The Terminal couldn't find the command -al

Hmm I tried to run the installer and just got this method: ```
 No installer data could be found. If this problem persists, please contact Blizzard Technical Support.

```

NB: Just right clicked > Properties on the example folder and it says it's only 117mb, what happend to the other 7.1gb it should have mounted along with it o.0 ?

edit: How do I unmount it now, it's throwing me up an error about fstabbing and not being root.

---

### Post by Blue Summer on 2010-11-02
Sorry to bump :)

---

### Post by matt_symes on 2010-11-02
Hi

sudo umount  /pathto/mountpoint (From the previous posts)

BTW

**ls -al**

Kind regards

---

### Post by Blue Summer on 2010-11-02
Thanks for the unmounting code.


Just copied and pasted what you put and this is the error I get.
```
rej3kt@Rej3kt:~$ ls -al /home/Rej3kt/Desktop/
ls: cannot access /home/Rej3kt/Desktop/: No such file or directory

```

---

### Post by matt_symes on 2010-11-02
Hi
[FONT=monospace]
[/FONT]> ls -al /home/Rej3kt/Desktop/try this. rej3kt (lower case r)

ls -al /home/rej3kt/Desktop/

And i'm glad it's all fixed now

Kind regards

---

### Post by Blue Summer on 2010-11-02
Heya, the output is this after doing whatcha said ```
rej3kt@Rej3kt:~$ ls -al /home/rej3kt/Desktop/
total 7530660
drwxr-xr-x  7 rej3kt rej3kt       4096 2010-11-02 14:48 .
drwxr-xr-x 52 rej3kt rej3kt       4096 2010-11-02 18:15 ..
drwxr-xr-x  3 rej3kt rej3kt       4096 2010-10-24 10:10 C++ Class
drwxr-xr-x 11 rej3kt rej3kt       4096 2010-10-16 11:09 college stoof
drwxr-xr-x 10 rej3kt rej3kt      12288 2010-10-05 14:13 Downloads
lrwxrwxrwx  1 rej3kt rej3kt          8 2010-10-28 10:24 Link to www -> /var/www
lrwxrwxrwx  1 rej3kt rej3kt         18 2010-05-09 20:55 Music -> /home/rej3kt/Music
-rw-r--r--  1 rej3kt rej3kt     766913 2010-10-31 19:12 networking.odp
-rw-r--r--  1 rej3kt rej3kt     832000 2010-11-01 09:46 networking.ppt
-rw-r--r--  1 rej3kt rej3kt        115 2010-06-08 14:08 new file
-rw-r--r--  1 rej3kt rej3kt     139264 2010-10-16 11:21 Object_Oriented_Programming_Assignment_0910.doc
-rw-r--r--  1 rej3kt rej3kt      51920 2010-10-27 10:00 pear.jpg
drwx------  3 rej3kt rej3kt       4096 2010-10-24 12:08 person
-rw-r--r--  1 rej3kt rej3kt 7708278784 2010-07-31 01:14 sc.iso
-rw-r--r--  1 rej3kt rej3kt     115815 2010-10-29 10:47 Screenshot-1.png
-rw-r--r--  1 rej3kt rej3kt     985600 2010-10-22 12:06 Screenshot.png
drwxr-xr-x  4 rej3kt rej3kt       4096 2010-11-02 14:48 starcraft2
-rwxr-xr-x  1 rej3kt rej3kt        338 2010-04-10 09:59 Steam.desktop
-rw-r--r--  1 rej3kt rej3kt      74752 2010-11-01 09:46 Task 1.doc
-rw-r--r--  1 rej3kt rej3kt      79863 2010-10-31 11:26 Task 1.odt
-rwxr-xr-x  1 rej3kt rej3kt        288 2010-11-02 19:54 World of Warcraft.desktop

```


Also I'm afraid it's not fixed as the mounting only mounted 117mb out of 7.2gb of what it should have done! Everything is so complicated! lol.

---

### Post by matt_symes on 2010-11-02
Hi

No worries. We don't really need this now as your problem is fixed. But it is good you can list the contents of a directory using a terminal. Remember Ubuntu is case sensitive, so when you type anything in at the terminal it has to be typed exactly, including paths.

Keep learning and having fun.

Kind regards.

---

### Post by matt_symes on 2010-11-02
Hi

No worries. We don't really need this now as your problem is fixed. But it is good you can list the contents of a directory using a terminal. Remember Ubuntu is case sensitive, so when you type anything in at the terminal it has to be typed exactly, including paths.

Keep learning and having fun.

> Also I'm afraid it's not fixed as the mounting only mounted 117mb out of  7.2gb of what it should have done! Everything is so complicated! lol.Sorry missed that bit...

Without looking at the iso i really cant tell. 
But the iso size is

-rw-r--r--  1 rej3kt rej3kt 7708278784 2010-07-31 01:14 sc.iso

And sorry for the double post. Its late here

Kind regards.

---

### Post by Blue Summer on 2010-11-03
Thanks for the help Matt.

Still stuck on mounting this as it's only mounting 117mb out of 7.2gb that should be mounting.

---

### Post by matt_symes on 2010-11-03
Hi

Mount the iso as before. Open a terminal and type

du -s -m /media/example

This will give you the disk usage for the mounted iso in MB (assuming its still mounted at /media/example).

Post the results back.

Kind regards

---

### Post by Blue Summer on 2010-11-03
This is what I got : ```
rej3kt@Rej3kt:~$ du -s -m /media/example
116	/media/example

```

---

### Post by matt_symes on 2010-11-03
Hi

Well you are right. That is the disk usage for the iso. 

Are you sure this is not the size of the game? 

You might not be having any issues here. The iso's size may be 7 Gb on your hard drive but the files within that iso are showing only 116 MB. I am not sure if this is an issue.

The iso was mounted as a loopback device. The size of the files contained within the iso can be smaller than the size of the iso itself.

Kind regards

---

### Post by Blue Summer on 2010-11-03
Sorry to be a noob but I'm not sure what a "loopback" device is.

Also the game is 99% likely to be around the 7gb mark it's a new one.

---

### Post by coffeecat on 2010-11-03
I wonder if this is some sort of anti-piracy measure. If you make an ISO of the Vista install DVD, you get an ISO file of 2.9GB. If you open the ISO with archive mounter or archive manager, all you see is a single README.TXT file of 135 bytes.

---

### Post by matt_symes on 2010-11-03
Hi

Alright, Loop devices. This is a _basic_ description for files. There are a number of loop devices.

In ubuntu it is possible to create a file on the current filing system. This file can then be mounted like any partition or other media. One can format this file using, say, ext4. And through the mount point files can be saved into it as if it were a filing system in its own partition.
In effect what you have is a filing system within a file on a filing system on a partition.

Say the above steps were followed and a file 10M was created formatted and mounted. 
Say 2 files 1M each were saved in that files filing system.
One would then have the situation where there was a 10M file on the main filing system.
Within the 10M files filing system there would be 2 1M files, a disk usage of 2M for that mounted loop device.
2M inside 10M inside the filing system on the partition.

Does that make any sense?

As for your game, have you tried to play it?

Kind regards

---

### Post by matt_symes on 2010-11-03
Hi

Hi coffecat. 

I was wondering that but he did say the game was legal, so...

Kind regards

---

### Post by Blue Summer on 2010-11-03
Well I didn't exactly think anyone would help if I said I had a Razor copy of Starcraft 2 lol.

---

### Post by matt_symes on 2010-11-03
Hi

No worries. As long as you have learnt something.

Kind regards

---

### Post by coffeecat on 2010-11-03
> **matt_symes said:**
> Hi

Hi coffecat. 

I was wondering that but he did say the game was legal, so...

Kind regardsNo, I wasn't implying the game wasn't legal. :shock: I was wondering if some sort of security measure stops you peeping inside an ISO. Which is what may be going on when you make an ISO of the Vista DVD.

---

### Post by alphaamanitin on 2010-11-03
> **coffeecat said:**
> No, I wasn't implying the game wasn't legal. :shock: I was wondering if some sort of security measure stops you peeping inside an ISO. Which is what may be going on when you make an ISO of the Vista DVD.


Not sure but WinRAR will dump the entire contents of even Window Install DVDs (just did it with a legal copy of Windows 7).  WinRAR, though not actually free, is available for linux as a command line interface only.  

But here is a different though, why not try a virtual drive software, or simply find a friend or some one who can burn it off for you?

> **Blue Summer said:**
> Well I didn't exactly think anyone would help if I said I had a Razor copy of Starcraft 2 lol.

Though if that is true, then maybe he won't be mounting it exactly because of security safe gurads. I know StarCraft II does have quite a bit of that type of thing.

AlphaA

---

### Post by Blue Summer on 2010-11-04
Yeah I think I'll give up with this ISO and try find a mate to burn it to disc with a dual layer writer. I've got winrar installed in wine for some reason as well. Thanks for all the help guys =)

---

