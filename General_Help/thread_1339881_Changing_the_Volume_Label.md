---
title: "Changing the Volume Label"
date: 2009-11-28
forum: General Help
---

### Post by mavigozler on 2009-11-28
I am trying to change the volume label, which contains a dreaded space character, of my external hard drive.  Have tried 'mlabel' under mtools (see output under [COLOR="MediumTurquoise"]NOTES/BACKGROUND[/COLOR]) and looked for 'ntfslabel' under the 'ntfsprogs' package (see attempt details under [COLOR="MediumTurquoise"]NOTES/BACKGROUND[/COLOR]). Gparted is no help and using Windows is NOT an option (see [COLOR="MediumTurquoise"]notes[/COLOR] below).

[COLOR="Red"]What do I do?  [/COLOR]


**[COLOR="MediumTurquoise"]NOTES/BACKGROUND[/COLOR]**

I just had a major problem trying to use **autopsy/sleuthkit** to examine a Windows Vista system disk image, probably because the path had whitespace (a space character) in it.  The web interface wants a path to the disk image, but is choking on the space character.  I can reference the path in any terminal session command line, such as changing directory by

```
$ cd /media/WD\ 1TB
```

but clearly HTML form input submission does not work similarly.

The volume label got the space character in it because some time ago, I used the features of the file management application of the Microsoft operating enviroment (my hateful way of expressing "...used Windows Explorer of the Vista system...") to name my 1 TB USB external hard drive.  Windows does not think anything of accepting a volume label like "WD 1TB"---yes, with a space character--and does not inform the user that one day he might regret it.  (Note WD refers to Western Digital, the drive manufacturer.  

I later put on Ubuntu 9.04 on this drive, in about 200 GB space of the drive, installed with GRUB as well.

Here is the **fdisk -l** output on this drive:

```
Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x03ec68e0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       97261   781248951    7  HPFS/NTFS
/dev/sdc2           97262      121601   195511050    5  Extended
/dev/sdc5           97262       97504     1951866   82  Linux swap / Solaris
/dev/sdc6   *       97505      101151    29294496   83  Linux
/dev/sdc7          101152      121601   164264593+  83  Linux
```

[COLOR="Green"]Gparted[/COLOR] GUI shows the label in /dev/sdc1 is 'WD 1TB' and selecting this line with the mouse device and using right mouse button click popup menu shows the 'Label' command disabled.  /dev/sdc is in the unmounted state.  Note [COLOR="Green"]gparted[/COLOR] shows many packages and their utilities not installed or unavailable.

[COLOR="Green"]Gparted[/COLOR] reports **"DiskLabelType: msdos"** for /dev/sdc.  The use of '[COLOR="Green"]mlabel[/COLOR]' in mtools, as specified in [[COLOR="Blue"]https://help.ubuntu.com/community/RenameUSBDrive[/COLOR]]("https://help.ubuntu.com/community/RenameUSBDrive"), just to read the label produced the following output:

```
$ sudo mlabel -i /dev/sdc -s ::

init :: non DOS media
Cannot initialize '::'
mlabel: Cannot initialize drive
```

The label is shown by [COLOR="Green"]GParted[/COLOR] to be on /dev/sdc1, which is **NTFS**. [[COLOR="Blue"]This forum thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1330119&highlight=volume+label") points to this web document [**[COLOR="Blue"]Change your NTFS / windows drive label via linux[/COLOR]**]("http://tuxecute.blogspot.com/2008/09/change-your-ntfs-windows-drive-label.html") but Synaptic PM and the command line 'sudo apt-get install ntsfprogs' shows no such package available in Ubuntu repositories.

---

### Post by jamesisin on 2009-11-28
You have to unmount the drive to change the label, I believe.

---

### Post by raktarok on 2009-11-28
I can install that package ntfsprogs in my system. here's the url for the packages(along with the dependencies), if you need it:
[http://mirrors.rit.edu/ubuntu/pool/main/l/linux-ntfs/libntfs10_2.0.0-1ubuntu3_i386.deb](http://mirrors.rit.edu/ubuntu/pool/main/l/linux-ntfs/libntfs10_2.0.0-1ubuntu3_i386.deb)
[http://mirrors.rit.edu/ubuntu/pool/main/l/linux-ntfs/ntfsprogs_2.0.0-1ubuntu3_i386.deb](http://mirrors.rit.edu/ubuntu/pool/main/l/linux-ntfs/ntfsprogs_2.0.0-1ubuntu3_i386.deb)'

---

### Post by mavigozler on 2009-11-28
Device was supposedly unmounted during all attempts.

However, the following output is shown to **mount** command:

```
$ mount -l
/dev/sdc6 on / type ext3 (rw,relatime,errors=remount-ro) []
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-16-generic/volatile type tmpfs (rw,mode=755)
/dev/sdc7 on /home type ext3 (rw,relatime) []
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/mavigozler/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=mavigozler)
/dev/sr0 on /media/USR9108 1.0 type iso9660 (ro,nosuid,nodev,uhelper=hal,uid=1000,utf8) [USR9108 1.0]
```

---

### Post by jamesisin on 2009-11-28
Can you try specifying sdc6 in your unmount command?

---

### Post by mavigozler on 2009-11-28
/dev/sdc6 is actually the partition to the Ubuntu root filesystem.

I had a feeling that if I told the computer to disconnect itself from its filesystem---its executables, config files, etc---it might have some kind of spasm.

So after reading (and not really comprehending the full significance of) the info on umount, I decided on:

$ umount -fl /dev/sdc6

Suddenly the drive starts to make noises and everything on the screen freezes (mouse cursor).  The terminal is takes no keyboard input.

The only thing left is to press down the power button and re-boot.

I am filing this away under IMPORTANT LESSONS:  Never u[n]mount the file system or any other partition used by the system.

---

### Post by mavigozler on 2009-11-28
1. I went back to Synaptics PackMan and found ntfsprogs, and installed it.
2. Re-opened GParted, which indicated file system support for NTFS.
3. In GParted, selected /dev/sdc1 which had the label 'WD 1TB'
4. The popup menu (right mouse button) NOW showed the Label command active.
5. Renamed 'WD 1TB' to 'WD1TB'
6. Applied changes

The volume would not mount (uh oh!)

7. Did a machine re-start and volume labeled 'WD1TB' mounted itself.
8. Clicked on file browser to make sure everything was there and accessible (it was)

The autopsy web interface then immediately found the disk image file and now I am relieved.

---

### Post by QLee on 2009-11-28
mavigozler,

I see you are happy with your system and that's great but I want to point out that space is an allowed character in a volume label. The system I'm typing this on has 5 different volumes with a space character in the label. We don't want people reading this to get a wrong idea.

---

### Post by mavigozler on 2009-11-28
I agree that whitespace (including space character) can be used in the volume name, and the filesystem can reference it through the Linux/Ubuntu GUI or CLI.

Here's the problem (see my first post):

**Autopsy** is a web interface to sleuthkit, and the server receives user input through submitted HTML forms of the HTTP client of your choice.  It requires that the user provide a disk image file created by other means (I used **ddrescue** to create the image).

My disk image file was in the filesystem through the path:

  [COLOR="Blue"] /media/WD\ 1TB/diskImages/CDrive.image[/COLOR]

When I put this into the **autopsy** HTML form, the server reported a bad path.

When I was able to rename the label so that the path to the image file was

 [COLOR="Blue"]  /media/WD1TB/diskImages/CDrive.image[/COLOR]

then **autopsy** had no problem at all accepting form input (and adding the image file).

I suppose I could have looked at the **GET** or **POST** HTTP request that the browser might send to see how the form was submitting the text control input and figure out a way for **autopsy** to interpret the URL as the local file, but it was supposed to be easier just changing the volume label to remove whitespace.

Note that URL encoding such as
[COLOR="Blue"]
   /media/WD[COLOR="Red"]%20[/COLOR]1TB/diskImages/CDrive.image[/COLOR]

was just as ineffective as

[COLOR="Blue"]   /media/WD[COLOR="Red"]\ [/COLOR]1TB/diskImages/CDrive.image[/COLOR]

Perhaps the **autopsy** server could provide info/help on how to include paths (URIs) that include non-printable characters.  I did not find it.

---

### Post by QLee on 2009-11-28
[QUOTE=mavigozler]I agree that whitespace (including space character) can be used in the volume name, and the filesystem can reference it through the Linux/Ubuntu GUI or CLI.[/QUOTE]
And, as I stated, I was just commenting to make sure people didn't misunderstand your use of "dreaded"

Don't know if it would have worked or not but did you try enclosing WD%201TB in quote characters similar to the way you used %20 for space? 

I did read your post.

---

### Post by mavigozler on 2009-11-28
> **QLee said:**
> Don't know if it would have worked or not but did you try enclosing WD%201TB in quote characters similar to the way you used %20 for space?

I think I might have attempted many variations, although I suspected that the quote character itself would just make things worse (i.e., be encoded).

The URL-encoding mechanisms used by the HTTP client in HTML form submission, if not modified by client-side Javascript in some way, or intelligently handled on the server side, are nonetheless entirely different from Unix shell command line processing unfortunately.

---

### Post by QLee on 2009-11-28
Okay then, I was just quessing. I will accept your word that %23WD%201TB%23 would not work.

I generally don't like avatars, however, for some reason yours appeals to me. Maybe I feel good about the colors.

---

### Post by ed-koala on 2009-11-28
A simple solution to changing a volume label is just boot from a live CD, unmount the drive if it mounts, then run gparted and change the label. Very easy ... did it myself for my external drive in just a few minutes.

---

### Post by jamesisin on 2009-11-28
Haha, oops.  Sorry, man.  I didn't realize you were dealing with your boot partition.

Yeah, don't unmount your boot partition while booted.

The Live CD suggestion would have been useful in your case.  Glad you were able to work things out.

---

