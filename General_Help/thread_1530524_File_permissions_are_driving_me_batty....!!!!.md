---
title: "File permissions are driving me batty....!!!!"
date: 2010-07-13
forum: General Help
---

### Post by tonewheelkev on 2010-07-13
Can only read files on USB stick, and USB Drive.....can't copy, move or delete them due to restrictions/file permissions...."You are not the OWNER...." etc

Can I remove ALL such permissions....I am the ONLY user of this machine!?

Please reply in a way that a 5 year old may understand.....REALLY!!!!

This is getting SOOOOOOOO frustrating...........

Ta!!!

---

### Post by bodhi.zazen on 2010-07-13
HAHAHAHAHAHA !!!

I recall that feeling when I ran into permissions as well.

See:  [http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

The problem you have is that I assume your USB is FAT or NTFS, so chown / chmod will not work.

with FAT and NTFS, permissions should be set at the time of mounting, and should be automatic.

So you have some kind of a problem with some of the more esoteric portions of Linux.

Or else you made an entry in fstab ?

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131") 

You can always fall back to

```
gksu nautilus
```

but you should learn permissions asap

---

### Post by belkinsa on 2010-07-13
> **tonewheelkev said:**
> 
Please reply in a way that a 5 year old may understand.....REALLY!!!!


Wow, a five year old?!  You rock man!  :guitar:  You will be a wiz when you hit school!

---

### Post by prodigy_ on 2010-07-13
The simple answer is no, you can't remove permissions from Linux (ext) just as you you can't remove them from **any** modern file system. (Ok, FAT doesn't have them at all but it's a legacy file system.)

---

### Post by tonewheelkev on 2010-07-13
Thanks?........

---

### Post by tonewheelkev on 2010-07-14
> **bodhi.zazen said:**
> HAHAHAHAHAHA !!!

I recall that feeling when I ran into permissions as well.

See:  [http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

The problem you have is that I assume your USB is FAT or NTFS, so chown / chmod will not work.

with FAT and NTFS, permissions should be set at the time of mounting, and should be automatic.

So you have some kind of a problem with some of the more esoteric portions of Linux.

Or else you made an entry in fstab ?

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131") 

You can always fall back to

```
gksu nautilus
```

but you should learn permissions asap
Still totally stuffed with this.......

Tried:

gksu nautilus (whatever that is....!?) to no avail....but thanks anyway

---

### Post by JohnDMcClane on 2010-07-14
> **Mechafish said:**
> Wow, a five year old?!  You rock man!  :guitar:  You will be a wiz when you hit school!

Agreed :KS

---

### Post by tonewheelkev on 2010-07-14
Thanks [JohnDMcClane]("http://ubuntuforums.org/member.php?u=1097101")

......very helpful......

---

### Post by bodhi.zazen on 2010-07-14
> **tonewheelkev said:**
> Still totally stuffed with this.......

Tried:

gksu nautilus (whatever that is....!?) to no avail....but thanks anyway

My guess, if gksu nautilus did not work, is you have a hard ware problem of some kind or a problem with hal/udev, hard to know.

gksu starts graphical applications, in this case nautilus, as root and so you should be able to copy / past files.

If it is a permissions problem you may be able to fix it by editing fstab and / or remounting the device.

---

### Post by SciFi-Bob on 2010-07-14
Normally all user mounts of usb sticks and such, are no problem, but if you have some custom mount options in /etc/fstab, or the file system on the stick is NTFS, it can be frustrating.

The quick fix can be:

sudo chown -R {youruser} {mountpoint}/*

Example:

You have mounted your usb stick into /media/USB1, and you are user 'garfield'

Issue this command:

sudo chown -R garfield /media/USB1 

Then all files on the usb stick should belong to you.
(depends on the mount options though..)

"gksu" is a (gui) command to execute anything as root.
"gksu nautilus" would run nautilus (the file manager) as root, so that you get full access to your files.

---

### Post by Morbius1 on 2010-07-14
Excuse the interruption but this external USB storage device - how is it formatted?

FAT32, NTFS, EXT2, EXT3, ...

It makes a difference. You can chown or chmod an ext2/3 partition. But you can't on a FAT32 or NTFS partition. From the sound of it it's an ext2 or ext3 partition. But that's relatively rare unless you formatted it yourself.

---

### Post by WorMzy on 2010-08-22
Can you plug in the drives, mount them, then copy and paste the contents of /etc/mtab here. May help if you open a terminal (Applications -> Accessories -> Terminal) also post the output of ```
sudo blkid
```

Put [CODE[COLOR="Black"]][[/COLOR]/CODE] tags around each block of text/output so it's easier to read please. :)

---

### Post by renkinjutsu on 2010-08-22
Check your UID with ```
echo $UID
```, then mount your usb stick or whatever with the option uid=youruid.. example ```

# echo $UID
1000
$ mount -o uid=1000 /dev/usb /mnt/usbstick
```
Then now you should be able to access the files with your user

---

### Post by tonewheelkev on 2010-08-22
Output of sudo blkid (....pardon!!)
I have probably cocked this up....am afraid of the terminal window!


kev@kev-desktop:~$ sudo blkid
[sudo] password for kev: 
/dev/sda1: UUID="9b61335a-e083-4f91-974c-fe76727904dc" TYPE="ext4" 
/dev/sda5: UUID="b782367d-d18c-4f1d-a11b-7a1e66b5cf46" TYPE="swap" 
/dev/sdc1: SEC_TYPE="msdos" LABEL="KEVIN" UUID="6A60-5B97" TYPE="vfat" 
kev@kev-desktop:~$ 


.....as for the contents of /etc/mtab.....now I'm really lost...
Kev

---

### Post by WorMzy on 2010-08-22
Don't be afraid of the terminal, it's a very useful tool. You ran the blkid command fine. :)


You can view the contents of mtab by entering the following command into a terminal:

```
cat /etc/mtab
```

Or just open the file in a text editor.

---

### Post by tonewheelkev on 2010-08-22
Here 'tis...


kev@kev-desktop:~$ cat /etc/mtab
/dev/sda1 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
none /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/kev/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=kev 0 0
/dev/sdc1 /media/usb0 vfat rw,noexec,nodev,sync,noatime,nodiratime 0 0
kev@kev-desktop:~$

---

### Post by richs-lxh on 2010-08-22
You have a Fat32 file system on that drive:

> /dev/sdc1 /media/usb0 vfat rw,noexec,nodev,sync,noatime,nodiratime 0 0

I suggest having a look at this link about mounting Windows file systems. Works for internal and external drives:
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

But first, try this command to mount the drive:
sudo mount -a

Then use the "gksu nautilus" command to open the file browser as root and go to /media/usb0 and see if you can see the files, and if you have read and write access.

If not, I would create a file in the "mnt" directory called "storage" and then follow the guide on psychocats.net

---

### Post by tonewheelkev on 2010-08-22
> **richs-lxh said:**
> You have a Fat32 file system on that drive:



I suggest having a look at this link about mounting Windows file systems. Works for internal and external drives:
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

But first, try this command to mount the drive:
sudo mount -a

Then use the "gksu nautilus" command to open the file browser as root and go to /media/usb0 and see if you can see the files, and if you have read and write access.

If not, I would create a file in the "mnt" directory called "storage" and then follow the guide on psychocats.net
.....Gasp!!!!!!!!

---

### Post by WorMzy on 2010-08-22
Good gasp or bad gasp?

Problem solved?

I was going to suggest making an entry in fstab with slightly altered mount parameters. E.g.

```
UUID=6A60-5B97 /media/KEVIN vfat noauto,rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush 0 0
```

Of course, you'd need to make the /media/KEVIN folder for it to mount into.

But if you've found another solution, great. :)

---

### Post by tonewheelkev on 2010-08-22
....it was bad gasp!!!....I'm afraid.
I've now used terminal twice only....following you instructions, 
and richs-lxh's instructions are baffling to me.....

---

### Post by richs-lxh on 2010-08-22
The terminal can seem a bit daunting. But don't worry, it's quite simple once you get used to it.

Open the Terminal and type:
> gksudo nautilus

Press "Enter" and your (Nautilus) file manager will open.

Next just go to the Folder /media/usb0

It's more or less the same as with Windows when you open folders with the file manager and you see all the folder icons.

If you would like to try and see what's in that folder in the terminal, you can use the command "ls" followed by the directory, ie:
> ls /media/usb0

And  a list of all the files will appear.

Just like:
> ls /home/kevin
Would show all the files in your home directory.

But it's just as easy to navigate with the file manager.

PS: Ubuntu is setup by default to open any USB drive you plugin, so it's not normally this difficult.

---

### Post by bodhi.zazen on 2010-08-22
> **tonewheelkev said:**
> ....it was bad gasp!!!....I'm afraid.
I've now used terminal twice only....following you instructions, 
and richs-lxh's instructions are baffling to me.....

LOL !!! :lolflag:

Command line phobia is a serious symptom of Windows addiction.

Another misconception is that you *must* use the command line. Many users here never use the command line.

Most people find a happy balance in between those extremes.

When you have time , take a look at the basics. I found linuxcommand was helpful, you may find the second half to be too much, but at least the first few sections help.

[http://linuxcommand.org/](http://linuxcommand.org/)

The benefits of using the command line are :

1. It is easier to assist people by posting a few commands rather then describe all the mouse clicks or post screen shots.

2. The command line is helpful, if for example, if you get an err message post it here. While you may not understand it, many herre will, and we can explain it to you.

Keep in mind, how many years have you used Windows ? I usually advise people use Linux and the command line for 3-6 months. Understand you are on a steep learning curve right now, it does get easier.

If the command line is not going to work for you, try the wiki. Often on the wiki people take the time to post screen shots, for example :

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

Some screen shots there, but on some of the sub-pages or linked pages you find more :

[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

Others have posted graphical how-to's in youtube (or similar screencasts).

and on, so many things are graphical these days, it is just a bit tedious to post screen shots of a default Ubuntu install on the forums.

When you run across something you do not understand, ask, If the answer is geekspeak, ask for clarification.

---

### Post by WorMzy on 2010-08-22
Okay, lets see if this helps:

Press Alt+F2 to bring up the run dialogue box, and open your fstab file with this command
```
gksu gedit /etc/fstab
```

You now have a very important file opened as the root user, so _don't edit any of the existing lines_ or you may break something necessary for the system to work.

Add a new line at the bottom of the file, and copy-paste this there:

```
UUID=6A60-5B97 [COLOR="Red"]/media/KEVIN[/COLOR] vfat noauto,rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush 0 0
```

Save the file and close the text editor.

Now open a terminal and create the folder we talked about earlier with this command:

```
sudo mkdir [COLOR="Red"]/media/KEVIN[/COLOR]
```

Finally, unplug your USB drive, then plug it back in. If it doesn't mount automatically, you'll need to open the file browser (nautilus) and manually mount it by clicking on it's name in the left-hand [side pane]("http://img842.imageshack.us/img842/543/20100822155042802x573sc.png").

Does it let you edit files now?

* Oh, and the red text needs to be the same in both places. So if you'd rather have a different folder name, feel free to use a different one, but make sure that you use the same folder name in both places.

---

### Post by tonewheelkev on 2010-08-22
ALT + F2 brings up a RUN APPLICATION window.....is this correct?
Kev

---

### Post by bodhi.zazen on 2010-08-22
> **WorMzy said:**
> Okay, lets see if this helps:

Press Alt+F2 to bring up the run dialogue box, and open your fstab file with this command
```
gksu gedit /etc/fstab
```

You now have a very important file opened as the root user, so _don't edit any of the existing lines_ or you may break something necessary for the system to work.

Add a new line at the bottom of the file, and copy-paste this there:

```
UUID=6A60-5B97 [COLOR="Red"]/media/KEVIN[/COLOR] vfat noauto,rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush 0 0
```

Save the file and close the text editor.

Now open a terminal and create the folder we talked about earlier with this command:

```
sudo mkdir [COLOR="Red"]/media/KEVIN[/COLOR]
```

Finally, unplug your USB drive, then plug it back in. If it doesn't mount automatically, you'll need to open the file browser (nautilus) and manually mount it by clicking on it's name in the left-hand [side pane]("http://img842.imageshack.us/img842/543/20100822155042802x573sc.png").

Does it let you edit files now?

* Oh, and the red text needs to be the same in both places. So if you'd rather have a different folder name, feel free to use a different one, but make sure that you use the same folder name in both places.

See also this wiki page :

[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

Adding an entry if fstab is the easiest solution I could find, there does not seem to be an easy way to set the ownership and permissions when auto mounting otherwise.

However, by default, when a usb drive is plugge din , by default the device should be mounted automatically and a nautilus window should open. You should own the files on the device.

I can not tell from your post if there is a problem with your system configuration or with your device. If you device has errors - either in the file system or with the hard ware - the device may be mounted ro.

Unmount the device and run fsck on it.

---

### Post by WorMzy on 2010-08-22
> **tonewheelkev said:**
> ALT + F2 brings up a RUN APPLICATION window.....is this correct?
Kev

Yes. Since that command is to open a GUI app I didn't see any point in getting you to use a terminal for it. You can use a terminal instead if you want, in this instance they can be used interchangeably, only command-line tools need to be run in a terminal (e.g. sudo mkdir). :)

---

### Post by tonewheelkev on 2010-08-22
....Yippeee....followed WorMzy's instructions, and can now send to USB!!

(Mind you, can't say I understand what I've done :lolflag: )

Thanks to all
Kev

---

### Post by WorMzy on 2010-08-22
I'm glad we could help.

Like richs-lxh said, it's not normally this difficult. All my USB drives have worked right out of the box, you've just been unfortunate. I'm not sure if this is the USB drive's fault, or if something has been set up incorrectly when you installed Ubuntu; but at least we've got it working now.

If you want to know what all the commands and stuff has been doing, just ask here and I'll write an explanation. :)

---

### Post by richs-lxh on 2010-08-24
> **tonewheelkev said:**
> ....Yippeee....followed WorMzy's instructions, and can now send to USB!!

(Mind you, can't say I understand what I've done :lolflag: )

Thanks to all
Kev

Great news. Now starts the fun stuff where you read up on what you have done. Not only will you be able to use the same technique for similar problems, but you'll also be able to help others :)

---

