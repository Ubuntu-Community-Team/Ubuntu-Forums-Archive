---
title: "Obtaining files from another partition"
date: 2010-03-22
forum: General Help
---

### Post by SlashHeist on 2010-03-22
Hello all...
       I was just wondering if there is a way to obtain files (music) from my Windows 7 partition without having to leave Ubuntu? I am on a Asus U50-A Laptop, dual booting with Windows 7 64bit (native OS on the machine) and Ubuntu 9.10 Karmic Koala 64bit. I want to get all my music from my Windows 7 account, cause frankly Ubuntu kicks Windows' *** and I don't want to use it at all any more except for the occasional use. 

Any ways to do this? Note to all I am Ubuntu noob! Cheers!:popcorn:

---

### Post by TitanusEramius on 2010-03-22
There are plenty of ways to do it ;)

But to be honest you probably will need to read a little about it, but in short you need to make sure you have the package installed with ntfs-3g, it's for reading the NTFS-filesystem Windows is using, and then you need to mount the partition with Windows to gain access to it.

A little reading:
(to install NTFS-support)
[http://www.howtoforge.com/ntfs_3g_ubuntu_feisty](http://www.howtoforge.com/ntfs_3g_ubuntu_feisty)
(to mount the Windows-partition)
[https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)

Mount can be a bit hard to grasp in the beginning, but with a little reading that should be no problem :D

Good luck

---

### Post by Hikayu on 2010-03-22
> **SlashHeist said:**
> Hello all...
       I was just wondering if there is a way to obtain files (music) from my Windows 7 partition without having to leave Ubuntu? I am on a Asus U50-A Laptop, dual booting with Windows 7 64bit (native OS on the machine) and Ubuntu 9.10 Karmic Koala 64bit. I want to get all my music from my Windows 7 account, cause frankly Ubuntu kicks Windows' *** and I don't want to use it at all any more except for the occasional use. 

Any ways to do this? Note to all I am Ubuntu noob! Cheers!:popcorn:


Welcome to the UbuntuForums,
I believe that there are many posts explaining this. 
You can access your other partition by typing :

```
mount -t vfat (Windows partition) (where to mount it)
```

I suggest you create a "Windows" directory on your Desktop, thus : 

```
mount -t vfat (Windows partition) /home/(UserName)/Desktop/Windows
```

It's likely that you Windows partition is "/dev/sda1" w/o quotes or "/dev/hda1" . Try both :

```
mount -t vfat /dev/sda1 /home/(UserName)/Desktop/Windows
```
And if it fails:
```
mount -t vfat /dev/hda1 /home/(UserName)/Desktop/Windows
```

---

### Post by Hikayu on 2010-03-22
And remember to replace "(UserName)" With your username. You get this by opening the terminal and seeing the first word before "@"

E.g: In:
```
hikayu@hikayu-desktop:~$ 
```
"hikayu" is my username.

---

### Post by 2hot6ft2 on 2010-03-22
I would just install ntfs-3g and ntsfprogs and browse the windows partition.
You can search for them in synaptic and install them or:
Open a terminal
Applications > Accessories > Terminal
and run
```
sudo apt-get install ntfs-3g ntsfprogs
```
Then you can click on Places > The windows partition (enter your password) and browse it.
In win 7 you get to the desktop by going to Users folder where it used to be Documents and Settings
Pic attached

---

### Post by SlashHeist on 2010-03-23
Awesome thanks guys. I will try all of your ideas since its always fun learning new things! Thanks again!

---

### Post by SlashHeist on 2010-03-23
Alright here is  another question relating to the same idea. I want to completely move over to Ubuntu. No more Windows at all. I looked up few a ways to do this but they were all for Jaunty Jackalope or some other version of Ubuntu... so I just wanted to double check. 

Seems like I will first back up all my data for Ubuntu and Windows (obviously). Then I will have to use my live CD and just basically do a fresh install over the entire drive. 

I have a 500gb HDD and 4gb of ram... so I want my swap to be 8gb, my partition mounted at "/" to have 50gb and my partition mounted at "home" to have the remaining (442gb). Is that correct or did I confuse something?

---

### Post by Blackbird_13 on 2010-03-23
If you really want to dump windows a fresh install from the live CD is straightforward. 

4gb of ram is plenty. I always use much less than the 1gb of my 4gb of ram. 

I suggest a swap partition size equal to ram size. I never get any swap usage, however, I believe with a laptop it is used for hibernation/suspend purposes. In any case, you won't need 8gb. 

"/" of 50gb is high compared to the recommendations I've seen - I have 10gb/12gb on my two pc's with no problem.

You may like to consider a "spare" partition for future use (alternate install/backup/etc).

You may find it useful to allocate your home directory to a separate partition. This allows you to do a re-install without having to re-create your home directory and personal settings.

I've only been using ubuntu for six months and found that after using it for a month or two I wished I had partitioned my drive differently -  so I just did a re-install, its easy!

Have fun.

---

### Post by srs5694 on 2010-03-23
> **SlashHeist said:**
> Alright here is  another question relating to the same idea. I want to completely move over to Ubuntu. No more Windows at all. I looked up few a ways to do this but they were all for Jaunty Jackalope or some other version of Ubuntu... so I just wanted to double check. 

Seems like I will first back up all my data for Ubuntu and Windows (obviously). Then I will have to use my live CD and just basically do a fresh install over the entire drive. 

There are at least two other ways to do it. Both begin with backing up or moving your user data from Windows, though. They then diverge:


[list]
[*]You can wipe the existing Windows partition (using GParted or a combination of fdisk and mkfs), mount it at some convenient location in your Linux directory tree, and use it for data storage without modifying your existing installation.
[*]You can delete your existing Windows partition (using GParted or fdisk), boot a Linux emergency disc, and resize your existing Linux partition(s) to fill the space formerly occupied by Windows.
[/list]


Details vary depending on how your system is currently configured and how you plan to use the system. For the first option, if you're currently using a smallish single-partition configuration (as is common for new Ubuntu users) with lots of space in the current Windows partition, you might want to move your /home directory to the former Windows partition. This isn't hard to accomplish, but it'll take a bit of file-juggling using an emergency disc or some tricks with account settings. Other options might be to use the Windows partition for part of the system or as a big empty partition mounted as a subdirectory of your home directory or in some other location.

The second option is a bit riskier, since any partition resize or move operation carries some unavoidable risks. The details of what needs to be moved depend on the current partition layout.

If you want more guidance on either option, you'll need to post details of your current layout. The output of a "sudo fdisk -l" may be enough, although if you've got multiple Linux partitions, the output of "df -h" may be necessary, too.

---

### Post by Mark Phelps on 2010-03-23
> **Hikayu said:**
>  ... I believe that there are many posts explaining this. 
You can access your other partition by typing :

```
mount -t vfat (Windows partition) (where to mount it)
```

Please do some RESEARCH before presenting solutions like this!

Win7 partitions are NTFS, not FAT! Attempting to mount an NTFS partition as VFAT, if it works (which I doubt) will almost certainly hose up the partition table!

---

### Post by Hikayu on 2010-03-23
> **Mark Phelps said:**
> ```
mount -t vfat (Windows partition) (where to mount it)
```

Please do some RESEARCH before presenting solutions like this!

Win7 partitions are NTFS, not FAT! Attempting to mount an NTFS partition as VFAT, if it works (which I doubt) will almost certainly hose up the partition table!

Oops, thanks for seeing my problem.

So it's :

[QUOTE=Mark Phelps;9015051]```
mount -t vntfs (Windows partition) (where to mount it)
```

Right?

---

### Post by TitanusEramius on 2010-03-23
> **Hikayu said:**
> Oops, thanks for seeing my problem.

So it's :

[QUOTE=Mark Phelps;9015051]```
mount -t vntfs (Windows partition) (where to mount it)
```Right?

In my opinion it's a bad practice just to write out examples of code, and I am not saying this to point any fingers, but I would like to know what the rest of you folks think about it since it's seems to be common practice.

For people who just learning to type in the terminal and is sitting on a hole new system, some random code can really mess things up and without any experience to pick out typos or bad ideas these people don't have a chance to sort out what to try, and what not to try.

---

### Post by srs5694 on 2010-03-23
> **Mark Phelps said:**
> Win7 partitions are NTFS, not FAT! Attempting to mount an NTFS partition as VFAT, if it works (which I doubt) will almost certainly hose up the partition table!

You're correct that Windows 7 is almost always installed on NTFS. (Maybe always; I'm not sure if it *can* be installed to FAT, although I'm pretty sure that Windows XP could be.) Attempting to mount NTFS as FAT, however, will result in an error message, with no damage done. What's more, even if a mount attempt with the wrong filesystem type somehow succeeded, it would be the partition's *contents* (that is, the filesystem) that would be damaged not the partition *table* (that is, the description of where partitions begin and end on the disk).

---

### Post by srs5694 on 2010-03-23
> **TitanusEramius said:**
> In my opinion it's a bad practice just to write out examples of code, and I am not saying this to point any fingers, but I would like to know what the rest of you folks think about it since it's seems to be common practice.

For people who just learning to type in the terminal and is sitting on a hole new system, some random code can really mess things up and without any experience to pick out typos or bad ideas these people don't have a chance to sort out what to try, and what not to try.

I disagree, for several reasons:


[list]
[*]Text-mode commands are concise and unambiguous (if typed correctly); it's often often easy to provide a one- or two-line example of commands that will do a job, vs. a page-long description of how to do the same thing with a GUI. The GUI procedure might be just as fast to implement in practice, but it takes longer to describe. This wastes time for both the person writing the procedure and the person(s) reading it.
[*]Text-mode commands are more likely to work across environments. The procedure to do something via a GUI in KDE might not be the same as the procedure to do the same thing in GNOME. Add other distributions to the mix and it gets even worse.
[*]At one level or another, most Linux administrative tasks deal with text-mode commands or textual configuration files. Using text-mode commands brings you closer to this core of what Linux is.
[*]Text-mode commands often provide options that may not be available in particular GUI interfaces. Sometimes these options are important for what the questioner wants to do.
[*]For all of the above reasons, the sooner new Linux users become at least passingly familiar with command-line tools, the better. GUI tools can help one get started, but to be truly fluent in Linux, you must know how to use a text-mode shell.
[*]Your point about text-mode commands being powerful and an easy way to get into trouble can be applied just as well to GUI tools. If you need to do something that requires root privileges, that task is dangerous whether you do it at a command line or via a GUI tool.
[/list]


Regarding safety, whether you're using a GUI or text-mode commands, if you need to type your password to do something (beyond typing your password to log in), there's the risk of damaging your system. This is true whether you use sudo at a command line or you launch a GUI tool and it asks for your password. In either case, you're essentially running the command or program as root (the superuser). Once you've done this, if a tool remains open (GUI or text-mode), it continues to be a risk. A general rule of thumb for text-mode programs is that whenever you type a command as root (via sudo in Ubuntu), you should type the command *without* hitting Enter, then remove your hand from the keyboard and review the command to be sure it's correct. If you're accessing a disk, did you type the correct filename? If you're deleting a file, is it the right file? If you're using a filename wildcard (*, ?, etc.), is it the right one? Only when you're sure that the command is correct and contains no typos should you hit the Enter key. You could phrase a similar rule for GUI tools, but it would refer to options in dialog boxes or items you click. Given GUI tools' variable interfaces, the equivalent to "hitting Enter" isn't constant; it could be "clicking OK" or "selecting File->Save" or something else. The same principles apply in both cases, though.

---

