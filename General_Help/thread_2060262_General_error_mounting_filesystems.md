---
title: "General error mounting filesystems"
date: 2012-09-19
forum: General Help
---

### Post by C3PO4 on 2012-09-19
Hey guys.
 
My friend ask me to repair her laptop. Of course I said yes, but she didnt mention she uses Ubuntu.
 
And Im completely new in Ubuntu world. Ive never used it. So I would appreciate any help. 
 
The laptop is Compaq 610 from HP, Intel Core 2 Duo 2000 Mhz, 3 Gb memory.
Version of Ubuntu: GNU GRUB version 1.99-21ubuntu3.1
 
And here is the problem:
 
I turn it on, select option "Ubuntu, with Linux 3.0.0-17-generic" and then I get:
 
mountall: /lib/x86_64-linux-gnu/libc.so.6: version ´GLIBC_2.14´not found (required by /lib/libply.so.2)
General error mounting filesystems.
A maintanenc shell will now be started.
CONTROL-D will terminate this shell and reboot the system.
root@Compaq-610:
 
I spent a week to find a solution how to repair it or at least back up all the data on the disc.
 
Unfortunatelly nothing worked. I tried recovery mode - fsck and I got the same mesage:mountall: /lib/x86_64-linux-gnu/libc.so.6: version ´GLIBC_2.14´not found (required by /lib/libply.so.2)
 
I tried to boot with LiveCD, it booted up, I choose Try Ubuntu......but I cannot open any of folder, because I dont have permission.... At least I would like to copy the data from the disc for my friend.
 
Can anybody help me with this? I am desperate.
 
Thank you very much!!!

---

### Post by twipley on 2012-09-19
Indeed, booting from the LiveCD sounds like a viable option.

There, you could fire up the terminal (CTRL+ALT+T), and gain required privileges so as to be up for the ahead tasks.

Running "sudo -s" there, you could chown things into place:

sudo chown -R <desired_owner_and_group_names> /media/<filesystem_label>

to change ownerships -- reported by "ls -l /media" -- to desired instances.

Perhaps better would just be to ALT+F2, and then to run the "gksu nautilus" command -- therefore popping up the file browser through pope-privileges -- and, from there, change permissions from the properties dialog.

Let us know how things are going, what worked, what did not, and let me be forgiven in the process for not having tested anything before handing it all to you in such a raw form.

Oh, and by the way welcome to the Ubuntu world. ):P

---

### Post by Bashing-om on 2012-09-20
C3PO4; Hi ! welcome to the forum.

  Here is an easier way to try and repair the file system:


We Will use Gnome Partition Editor (GParted) in your Ubuntu Live CD to effect this repair.
Always leave your file systems unmounted until after the file system check, never try to run a file system check in a file system while it's mounted.

    Insure that in your bios the boot options are set to boot cd first.
    Boot with the install disk. (insert install disk into cd device).
    @ greeter screen select "Try ubuntu"
          
    Open Gnome Partition Editor: dash->search term: GParted->Gparted Icon ->click
 and right-click on the partition you want checked. 
    Select 'check' from the right-click menu. If 'check' is greyed out you might need to select 'unmount first, then click 'check'.
    Click the 'Apply' check mark button up on the toolbar.
    Click the 'Apply' button in the confirmation pop-up window
    Watch the reciprocating bar for a few minutes, a very large file system may take a while
    Click on the 'Details' triangle to expand the window
    Click on the triangle in front of 'Check and repair filesystem (ext(X)_ on ....)' for details
    Be sure to fully expand all details and read what has been done. If it's the Ext4 file system, GParted will have calibrated your file system and run e2fsck -f -y -v on it for you, and has run resize2fs for you to make sure your file system is the right size to fill your partition.


We are here if you require further guidance or assistance .. Questions just ask !

[INDENT]welcome again to ubuntu from all of us ....BDQ
[/INDENT]

---

### Post by C3PO4 on 2012-09-20
Thank you guys for warm welcoming :-)
 
Well I opened GParted, checked and repaired file system (ext4) on /dev/sda1.....the disc has only 300Gb....
 
As you wrote Bashing-om, everything was done (calibration, e2fsck and also resizing)
 
After this I reboot the laptop without LiveCD, but it didnt help at all :-(
The same General error mounting filesystems warning appeared....
 
But I dont know if 32bit or 64bit Ubuntu is installed.....my Live CD is 64 bit.....you think this could be problem?
 
After this I tried what twipley wrote.
But I dont understand this one: 
"to change ownerships -- reported by "ls -l /media" -- to desired instances."
I dont know what to write? Just ls-I /media    into terminal?
 
I tried gksu nautilus as well.......this popped up: Sorry, there is nothing that matches your search!
 
:-(

---

### Post by C3PO4 on 2012-09-20
Also when I open 311Gb Filesystem and then right click on folder MEDIA, properties, there is only 1 item in it and under this is written (some contents unreadable) :-(
 
And one question: the data of my friend are only in this MEDIA folder? Or they can be somewhere else?
 
Thank you for your time ;-)

---

### Post by twipley on 2012-09-20
Well, "ls -l <path>" lists permissions, so you know if they have to be changed. If this is the case, then [chown]("http://linux.die.net/man/1/chown") through "chown -R ubuntu <files-path>" so as to take ownership of the files.

If I am not mistaken, "ubuntu" (or "1000") is the username used by the LiveCD.

sudo is pope-permissions acquisition (understandable through this [illustration]("http://xkcd.com/149/")).

"gksu nautilus" works here under the 12.10 beta-1 LiveCD, as I have just tried.

Let us know...
and good luck. ;)

EDIT: possibleness for data to be outside of /media, as I think the latter is reserved for separate partitions (or hardware) to be mounted there. It has to be said I am quite a layman to all this too; a social-sciences student almost just having started using Linux and Ubuntu.

Remember too that Linux is case-sensitive, so -r and -R are different command arguments, and /media and /Media are different paths.

---

### Post by jrog on 2012-09-20
> **C3PO4 said:**
> But I dont know if 32bit or 64bit Ubuntu is installed.....my Live CD is 64 bit.....you think this could be problem?
Responding only to this part, for the moment. It shouldn't be a problem, and it appears that 64-bit Ubuntu is installed anyway, because the system reports that it is looking for  /lib/**x86_64**-linux-gnu/libc.so.6

I suppose it's possible, though unlikely, that the installation itself is confused about whether it is 64-bit, though. It's very likely that you're dealing with a 64-bit installation.

---

### Post by jrog on 2012-09-20
> **C3PO4 said:**
> I turn it on, select option "Ubuntu, with Linux 3.0.0-17-generic"
Are there any other kernel options besides this one? (Not a recovery mode line, but a line with a different Linux version number.)

---

### Post by C3PO4 on 2012-09-20
> **jrog said:**
> Are there any other kernel options besides this one? (Not a recovery mode line, but a line with a different Linux version number.)
 
 
Yes, I can choose Previous Linux versions......and there are:
 
Ubuntu with Linux 3.0.0-16, 
3.0.0-14, 
3.0.0-12, 
2.6.38-11,
2.6.38-10,
2.6.38-8,
2.6.35-28
 
All these normal versions plus theirs recovery mode......but nothing works !!

---

### Post by C3PO4 on 2012-09-20
> **twipley said:**
> Well, "ls -l <path>" lists permissions, so you know if they have to be changed. If this is the case, then [chown]("http://linux.die.net/man/1/chown") through "chown -R ubuntu <files-path>" so as to take ownership of the files.
 
If I am not mistaken, "ubuntu" (or "1000") is the username used by the LiveCD.
 
sudo is pope-permissions acquisition (understandable through this [illustration]("http://xkcd.com/149/")).
 
"gksu nautilus" works here under the 12.10 beta-1 LiveCD, as I have just tried.
 
Let us know...
and good luck. ;)
 
EDIT: possibleness for data to be outside of /media, as I think the latter is reserved for separate partitions (or hardware) to be mounted there. It has to be said I am quite a layman to all this too; a social-sciences student almost just having started using Linux and Ubuntu.
 
Remember too that Linux is case-sensitive, so -r and -R are different command arguments, and /media and /Media are different paths.
 
Well, im going to try the "chown thing" .....
And what about the password she had?...
It is enough just to use chown and change file owner?

---

### Post by C3PO4 on 2012-09-20
Twipley, can you please be more specific what to write there:
sudo chown -R <desired_owner_and_group_names> /media/<filesystem_label>
 
desired owner and group names is like her nick name, which she used to use for loging in? Or it is name of the disc? In my case: 311 GB filesystem?
 
So:
 
sudo chown -R 311 GB filesystem/media/sda1 
 
Im sorry, im really novice ...

---

### Post by twipley on 2012-09-20
Okay, no problem.

When you right click a folder and select properties, on the permissions tab can be seen the current ones (user and group ownerships).

The same thing can be viewed using the "ls -l <path-to-file>" command. Remember that in Linux, folders are files, too.

Preamble, form the terminal you can see that your (albeit temporarily) user name is "ubuntu" -- the second name being the group name.

What is needed is for permissions to be changed, so that you can work with the files. To permit *everyone* to have *full* access to a folder and to *everything* that is included inside, run something such as:

```
chmod -R 777 /insert/desired/path/name/here
```

I guess just running "chmod -R 777 /" will change permissions for every file on the hard-disk drive, which is not a problem since the operating-system partition is going to be removed anyways, after the task (if I understood correctly).

From there one can perform backups as one wills. Also note that "sudo -s" might be needed in order for permissions to be gained to run the chmod command. Perhaps that one even has to write "sudo" in front of chmod.

It would be nice if you could report back on if that was needed or not.

Come back if that did not work, so that other people can help you. I will follow discussion in this case, though, out of interest.

---

### Post by C3PO4 on 2012-09-20
Thank you for answer twipley!
 
So I started with unmounting the disc, then opened terminal and wrote just
 
chmod -R 777 /
 
it was working for 5 minutes, but there was written that operation not permitted and also, that there is no free space for this ( I have no idea what space, because I was only chnaging permission, wasnt I)
 
There popped up new window saying: This computer has only 0 bytes disk space remaing :-(
 
Well, so I wrote exit, I opened it again and wrote sudo -s
 
I did the same again, I was happy because there was written, that the permission was change.......but after 2 minutes the window with no space popped up again....
 
So I restarted laptop, opened terminal, wrote sudo -s again hoping that it will be OK and permission will change for all her folders....
 
And that is what Ive got:
 
sudo: /etc/sudoers is mode 0777, should be 0440
sudo: no valid sudoers sources found, quitting
sudo: unable to initialize policy plugin
 
 
My guess is that something changed and something didnt and now I am in trouble....
 
What should I do next?

---

### Post by twipley on 2012-09-20
Okay -- so it seems there was need for sudo to be prefixed to the chmod command.

Meaning:

```
sudo -s
sudo chmod -R 777 /
```

If that is not working, then I really do not know what to do (except perhaps fiddling with the graphical "gksu nautilus" GUI-permission-changing path). Another way might be to try the following command, but that might well result in a similar error:

```
sudo chown -R ubuntu /
```

Or perhaps chowning or chmoding not whole root (/), but the home files (/home/<her-name>), because some users keep their complete data inside their home.

Or perhaps somebody else -- more experienced -- should be guiding you, because I am not even sure I am on the right path -- current being granting permissions.

EDIT: I guess that after running "sudo -s," the system may give you permission to navigate to any folder while inside the terminal (using the cd command then the absolute path), so that you can that way determine the user name she was using (if currently undetermined).

---

### Post by ezsit on 2012-09-20
I think that typing:

chmod -R 777 /

would try to change the permissions starting on the live media you booted from, and, being read only for certain parts of the filesystem, that would lead to an out of space message.

You might want to be more specific and use the chmod command on the /media/volume-name -- (where "volume-name" is the label of the filesystem)

chmod -R 777 /media/volume-name

Or, to be more specific:

chmod -R 777 /media/volume-name/home/username

That is, if the user's files are all in her /home directory.

Just a thought.

---

### Post by ezsit on 2012-09-20
>  Re: General error mounting filesystems
Thank you for answer twipley!

So I started with unmounting the disc, then opened terminal and wrote just

chmod -R 777 /

If you unmounted the disc and then ran the chmod command it would not have any effect on filesystems located on the unmounted disc. Also, can I assume you are booted from a liveCD or DVD?

> it was working for 5 minutes, but there was written that operation not permitted and also, that there is no free space for this ( I have no idea what space, because I was only chnaging permission, wasnt I)

There popped up new window saying: This computer has only 0 bytes disk space remaing

If you were booted from a live CD or DVD and ran the command:

sudo chmod -R 777 /

That command would start working on the filesystem on the live CD or DVD and being read only, it would run out of space.

> Well, so I wrote exit, I opened it again and wrote sudo -s

I did the same again, I was happy because there was written, that the permission was change.......but after 2 minutes the window with no space popped up again....

So I restarted laptop, opened terminal, wrote sudo -s again hoping that it will be OK and permission will change for all her folders....

And that is what Ive got:

sudo: /etc/sudoers is mode 0777, should be 0440
sudo: no valid sudoers sources found, quitting
sudo: unable to initialize policy plugin


My guess is that something changed and something didnt and now I am in trouble....

What should I do next?

I am not quite sure what you did here. Did you boot from a live CD or DVD and try to access the filesystem on the hard drive? If so, the error message does not make much sense. Did you try to boot from the hard drive? Most importantly, were any of the earlier steps done while booted from the hard drive? I am really unclear on what exactly you have done here. I am not trying to be rude, please understand that I want to help if possible. Thanks.

---

### Post by twipley on 2012-09-20
That is nice input, ezsit.

Indeed, "chmod -R 777 /media/volume-name" might be more appropriate to send than bare "chmod -R 777 /" -- the latter which has produced nothing good, since:
> **ezsit said:**
> If you were booted from a live CD or DVD and ran the command:

sudo chmod -R 777 /

That command would start working on the filesystem on the live CD or DVD and being read only, it would run out of space.

So, basically the first post of ezsit in this page is much relevant.

What I will do is just reboot using the LiveCD, then edit this post to report whether or not file systems automatically did get mounted to /media over here.

EDIT:

Please bear in mind that this is what I am using as a LiveCD: [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

I think I found the culprit. Indeed, as ezsit implied, extraneous file systems are not automatically mounted. An intuitive, graphical-interface method of mounting one is simply to press the folder icon in the launcher at the left, then left-click once on the device (e.g., 128 GB Volume).

Then, you can see it has been mounted by navigating to / (click on "file system" on the left bar of the file browser, which in fact is the LiveCD file system), then to /media. An "ubuntu" folder should now be present, which contains the mounted volume. This (/media/ubuntu) is the folder you might want to chown, chmod, or, for good measure, both.

Sorry though that I am not trying any of the offered-to-you commands, since I do not want to fiddle with important school stuff (this laptop is used for schooling). Also, I hope that the path opened in front of you is now more viable than ever. ;)

---

### Post by Bashing-om on 2012-09-20
C3PO4;
  Yeah thou you are setting before the greatest operating system the world has ever known and right now you are confused beyond measure; Be aware that there is no difficulties in ubuntu that can not be overcome.

If you would, let us simplify things:
 1. Is it your desire to repair the current operating system ?
  or 2. copy wanted files off the broken system and reinstall ?
  or 3. copy the wanted files and upgrade ubuntu or to another operating system ?

In the event that the interest is to copy off wanted files:
  open the file manager in the install cd ( how depends on the version you are using).
  The files systems that ubuntu can detect are listed in the left pane.
   explore around to identify the files you want to copy (whole directories may be copied)

  Then insert a usb thumb drive into a usb slot.
   the file manager automagically opens the thumb drive.

  drag and drop the files/directories from the broken system's windows TO the usb thumb drive's window. I expect that all the "user" files you desire to transfer will have no permissions issues "unless" your friend changed the permissions to keep them private.

If the desire is to repair the system... we can do that too. As the gui method did not work ...will take the CLI to effect a resolution and time/observation on your part to advise us of the exact errors and at what point in the booting process. (When you get the system repaired you may become an ubuntuite too). 

 Please bear in mind the CLI is not an ugly monster. It is a tool to master the operating system and bring out it's fuller capabilities. I will help you with the syntax of the commands, explaining what, where and why.

[INDENT]kind regards <==BDQ

[/INDENT]

---

### Post by twipley on 2012-09-21
Copying files through the method you have just described, but as you implied the possibility thereof, there indeeds seems to be a problem with permissions. From the first post:

> **C3PO4 said:**
> I tried to boot with LiveCD, it booted up, I choose Try Ubuntu......but I cannot open any of folder, because I dont have permission.... At least I would like to copy the data from the disc for my friend.

Of course, there are other methods, but to highlight it back:

> **twipley said:**
> Extraneous file systems are not automatically mounted. An intuitive, graphical-interface method of mounting one is simply to press the folder icon in the launcher at the left, then left-click once on the device (e.g., 128 GB Volume).

Then, you can see it has been mounted by navigating to / (click on "file system" on the left bar of the file browser, which in fact is the LiveCD file system), then to /media. An "ubuntu" folder should now be present, which contains the mounted volume. This (/media/ubuntu) is the folder you might want to chown, chmod, or, for good measure, both.

> **ezsit said:**
> chmod -R 777 /media/volume

---

### Post by Bashing-om on 2012-09-21
@ twipley; Yeah, I should have taken the time to catch up on this thread. My "excuse" too many irons in the fire at the same time. Slowing down at this time ...will pay more attention.

[INDENT][INDENT]regards <==BDQ

[/INDENT][/INDENT]

---

### Post by twipley on 2012-09-21
Indeed.

However, your contribution from that post looks quite useful.

Cheers! ):P

---

### Post by ezsit on 2012-09-22
Here are some general ideas to explore when trying to rescue data from an unbootable Ubuntu hard drive. Assuming that you wish to reinstall the operating system and just rescue files from a user's /home directory, and using a combination of the command line (terminal) and the graphical file manager.

First:

Get a Ubuntu LiveCD from [www.ubuntu.com](www.ubuntu.com), the newest version 12.04 will do just fine. Insert the CD and boot your computer from the CD. If this involves changing BIOS settings or using the BIOS boot menu, do so. 


[INDENT]*** Side Note ***
If using the LiveCD is not an option, I would suggest following the steps here:
	
[http://www.pendrivelinux.com/usb-parted-magic-flash-drive-creation-windows/](http://www.pendrivelinux.com/usb-parted-magic-flash-drive-creation-windows/)
	
In order to create a bootable USB flash drive with PartedMagic
*** End ***[/INDENT]

Second:

Once the computer has booted from the LiveCD you will have all the tools necessary. Ubuntu LiveCDs and PartedMagic will not automatically mount filesystems located on the internal hard drive(s) connected to the computer. Any USB drives WILL be automatically mounted during the boot from a LiveCD. All filesystems will get an drive icon on the Desktop or Taskbar.

If you mouse-hover over the drive icons you should see your mouse pointer change to a notification of the filesystem's size and possibly the label. Hover slowly enough so you can identify the desired filesystem to open.

To mount a filesystem simply click on the drive icon in the Taskbar and a file manager window will open at the mount point of the filesystem. From there you should see the directories and files located in the filesystem.

If you have a USB drive or external hard drive connected, click on its drive icon and a file manager window will open at its mount point. Hopefully, it should be a simple matter of dragging and dropping the desired folders from the source file manager window to the destination file manager window.

Dealing with filesystem problems:

Before starting this process, have a USB flash drive handy that is large enough to hold the anticipated files to be rescued. If clicking on the desired drive icon results in a filesystem level error preventing the mounting of the filesystem, the quickest and easiest response is to open a terminal window and perform the following sequence of commands:

**sudo fdisk -l**

This command will list (the argument passed to fdisk is a lower case L for listing) the drive devices detectable by the system. Internal hard drives will show up whether the filesystems are mounted or not. USB drives will only show up in the fdisk output when they are mounted. You might see something like:

[INDENT]Disk /dev/sda: 1000.2 GB, 1000203804160 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953523055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0004fb1a
	
Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     8194047     4096000   82  Linux swap/Solaris
/dev/sda2   *     8194048    16386047     4096000   83  Linux
/dev/sda3        16386048    98306047    40960000   83  Linux
/dev/sda4        98306048  1953521663   927607808   83  Linux
	
Disk /dev/sdb: 2038 MB, 2038431744 bytes
63 heads, 62 sectors/track, 1019 cylinders, total 3981312 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008cba4
	
Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          62     3980213     1990076    c  W95 FAT32 (LBA)[/INDENT]

In this example, /dev/sda is an internal hard drive with a total capacity of 1000GB or 1TB. Device /dev/sdb is a USB flash drive, with one partition, formatted fat32 and is 2GB in size. The hard drive has four primary partitions, all Linux filesystems and one swap. Now I know /dev/sda2 is 4GB, /dev/sda3 is 40GB and /dev/sda4 is 950GB, I also know /dev/sda2 is /boot, /dev/sda3 is /, and /dev/sda4 is /home. It may take some investigation to determine which devices contain which filesystems. Attempt to mount each filesystem and browse the filemanager and directory structure to determine where in the overall Unix filesystem you happen to be located.

On the Desktop the three Linux filesystems corresponding to /dev/sda2, /dev/sda3, and /dev/sda4 will appear as drive icons and you should be able to click on any one of them to mount them. If the one you wish to mount and copy data from does not mount because of some filesystem error, the fsck command may help. fsck is a filesystem checker and can fix many problems.

For example, I am using /dev/sda4 since I know this to be the largest filesystem and it contains the /home directory, the command:

**sudo fsck -fpv /dev/sda4**

This command needs to be run with sudo or root privileges and the filesystem needs to unmounted. The arguments -fpv tell the fsck command to run even if the filesystem was cleanly unmounted (f), to fix any problems (p) and to send verbose output (v).

In the case of my example, /dev/sda4 is 950GB and the fsck command will take several minutes to complete, be patient. The output in my case is:

[INDENT]fsck from util-linux 2.20.1
	
    9098 inodes used (0.02%)
     458 non-contiguous files (5.0%)
       3 non-contiguous directories (0.0%)
         # of inodes with ind/dind/tind blocks: 6657/4653/0
	18455681 blocks used (7.96%)
       0 bad blocks
       1 large file
	
    7670 regular files
    1410 directories
       0 character device files
       0 block device files
       0 fifos
       0 links
       9 symbolic links (9 fast symbolic links)
       0 sockets
--------
    9089 files[/INDENT]

The output does not indicate any problems fixed, but it would contain that information if applicable. After fsck finishes you should be able to mount the device in the graphical way as described above.

Dealing with permission problems:

OK, you have determined which device contains the /home filesystem and you have mounted that device but permission issues are preventing you from viewing and copying the files you want to your USB flash drive or other backup device. At this point, you are probably looking at two file manager windows open, one opened to the /home directory on the internal hard drive and the other window opened to your USB flash drive. The chmod command will change file permissions and work recursively, walking the filesystem and changing permissions throughout the directory hierarchy starting from /home/username.

Open a Terminal and change directories to the /media folder. Use the ls command to list the contents within the /media directory:

[INDENT]ezos@ezos:~$ cd /media
ezos@ezos:/media$ ls
cdrom  FAT32  fcf68892-f50e-45f0-90e7-d6484cb7ea4d
ezos@ezos:/media$[/INDENT]

In this case, the UUID of the filesystem on /dev/sda4 where my /home directory is located is the name of the directory we need to change into. If this is the case and you do not wish to type the entire UUID, you can select it with your mouse and use the Edit menu in the Terminal window to copy and paste the UUID into the cd command to avoid typos in the UUID. The terminal window may look like this when completed:

[INDENT]ezos@ezos:~$ cd /media
ezos@ezos:/media$ ls
cdrom  FAT32  fcf68892-f50e-45f0-90e7-d6484cb7ea4d
ezos@ezos:/media$ cd fcf68892-f50e-45f0-90e7-d6484cb7ea4d
ezos@ezos:/media/fcf68892-f50e-45f0-90e7-d6484cb7ea4d$ ls
ezos  lost+found  remastersys
ezos@ezos:/media/fcf68892-f50e-45f0-90e7-d6484cb7ea4d$[/INDENT]

I have used the ls command again once inside the /home directory to locate the user's directory from where we need to rescue files. So I can now use the chmod command to get inside the user's folder, and since the /home is located on its own partition, the command would look like this:

**sudo chmod -R 777 /ezos**

If the /home directory is in the / filesystem, the command would look like this:

**sudo chmod -R 777 /home/ezos**

This command will change the permissions only within the user folder for ezos. Afterwhich, you should be able to use the graphical file manager to browse, copy, and paste as needed to rescue the user's files to a USB flash drive or other backup device.

---

