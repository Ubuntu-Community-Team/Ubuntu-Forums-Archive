---
title: "Empty ISO directory after mounting"
date: 2010-01-27
forum: General Help
---

### Post by KarmicMeagan on 2010-01-27
I've looked everywhere and haven't found someone with a similar problem or even a hint to how to fix it or what's even going on.

I'm trying to mount the Sims 3 raw ISO so I can install the game with PlayOnLinux. Every program or method I've used to mount it seems to mount it successfully. My problem is, that when I go to open the mounted ISO image, the folder is empty and nothing comes up. Even when I go to rightclick > Properties, it displays the contents as nothing.

Has anyone else encountered this? I'm totally at a loss for what to do. :confused:

---

### Post by mechro on 2010-01-27
Where did you get the iso? Does it work in Windows?

---

### Post by KarmicMeagan on 2010-01-27
I downloaded it from a torrent. It was the same exact ISO I used when I had Windows and it mounted just fine in Daemon Tools Lite.

---

### Post by mechro on 2010-01-27
What happens if you right-click... Open with Archive Mounter. Does it appear in Places?

What happens if you right-click... Open with Archive Manager?

---

### Post by KarmicMeagan on 2010-01-27
When I right click and do Archive Mounter, like I said it acts like it's successfully mounted it as a drive. I double click it and nothing comes up but an empty folder with no visible or hidden files.

When I try Archive Manager, I get an error message: CD-ROM is NOT in ISO 9660 format.

The ISO itself is 5.6 GB.

---

### Post by adam814 on 2010-01-27
Well there's your problem...It's most likely a UDF filesystem.  A lot of DVDs are.

Try mounting it manually using the proper filesystem:
```
sudo mount -t udf -o loop /path/to/iso /mnt
```

---

### Post by KarmicMeagan on 2010-01-27
I'm not quite sure what what I got is supposed to tell me.

[FONT=Courier New][SIZE=1][B]Usage: mount -V                 : print version
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
For many more details, say  man 8 mount .[/B][/SIZE][/FONT]

---

### Post by adam814 on 2010-01-27
Hmm...I get that error if I type the command wrong (like leaving off the mountpoint at the end). If I try it on an ISO9660 .iso I get a different error (wrong fs type, which is expected).  If I try it with a UDF format .iso it works.

You could also try it without the "-t udf" parameter to see if it guesses correctly.

Also you could verify that it is in UDF format with "file /path/to/iso".  It would just label it as "data".

---

### Post by KarmicMeagan on 2010-01-27
Trying it without the -t udf parameter gives me this:

[B][FONT=Courier New]mount: can't find /home/meagan/sims/sims/TheSims3.iso in /etc/fstab or /etc/mtab

[/FONT][/B]And doing the file /path/to/iso gives me this:
[B][FONT=Courier New]
/home/meagan/sims/sims/thesims3.iso: ERROR: cannot open `/home/meagan/sims/sims/thesims3.iso' (No such file or directory)

[/FONT][/B]What it seems like to me is that the computer thinks there is no ISO file there at all. Despite the fact that the file is appearing and displaying a file size.

---

### Post by adam814 on 2010-01-27
In your post you're showing what would be to a Linux system two distinct files.  TheSims3.iso won't be the same as thesims3.iso.  First make sure you are using the right case for the full path.  Then try it again making sure you type the whole command.

---

### Post by KarmicMeagan on 2010-01-27
I thought the same thing and did both and got the same thing each time.

edit: I did it again and noticed I had missed a backslash. I got [B]/home/meagan/sims/sims/TheSims3.iso: data

[/B]edit: I then did the mount command again, and got this: **mount: according to mtab /home/meagan/sims/sims/TheSims3.iso is already mounted on /mnt as loop**

---

### Post by adam814 on 2010-01-27
And you don't see any files in /mnt?  You could try "sudo umount /mnt" and then re-mounting it.  If the files won't show up after that I'm not really sure where to go from there.

---

### Post by KarmicMeagan on 2010-01-27
Problem now is I don't know where to find /mnt 8-[

---

### Post by adam814 on 2010-01-28
In the terminal you'd just do "cd /mnt" and "ls" would show you the files in the directory.

In Nautilus you can go to "Filesystem" and it will be one of the folders.

---

### Post by guisardo on 2010-09-07
I was having the same issue.... I think that I was using the same iso too.
So, I installed Furius ISO. Selected the iso file and the options "Loop", "SHA1" and "Nautilus" and click mount.

To see the full content of the cd you'll probably have to use the terminal.

Regards

---

### Post by funenga on 2012-02-16
I was having trouble mounting via gui, so I did this:
```
cd /path/of/the/iso
sudo su
mkdir -p /mnt/tempDir
mount -t auto -o loop ???.iso /mnt/tempDir #substitute ??? with the filename
mount #list the mounted stuff, check the last line
```

Work with whats inside the iso, i.e., inside the folder "/mnt/tempDir".

Unmount:
```
sudo umount /mnt/tempDir
```

---

