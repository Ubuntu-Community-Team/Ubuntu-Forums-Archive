---
title: "Cannot mount partitions anymore"
date: 2010-08-24
forum: General Help
---

### Post by MusicMagic on 2010-08-24
[SIZE=3]Hi everyone,

I'm new here, and registered myself as an ancient Linux user to expand my knowledge, to contribute and seek some help for a few things that remain unsolved, like following issue:

First of all: it's been more than 12 years ago since I worked with Linux, and a lot has changed in the meantime. But I considered it a challenge to install Ubuntu 9.10 and lateron upgraded to 10.04 LTS without any troubles, until now:

Except my main partition ("/") all other partitions fail to mount. All NTFS partitions from my other OS and also 2 other linux ext4 partitions I've made are not accessible anymore. and, what bothers me the most: I deleted those 2 new linux partitions in the meantime because I couldn't access them initially because Root was the owner (Duh! root is standard disabled in Ubuntu, right?). After an attempt to try to automount all partitions following the help guides I got now big grey errors on my splashscreen while booting, telling that an error occured with e.g. /media/Backup because it is missing or it cannot be mounted, with 3 options below: waiting, skipping or using a command prompt to solve this. I always choose Skip for safety.

Now if I want to see the content of all my other partitions I got a popup telling me unable to mount e.g. /media/Downloads and the message included:
[/SIZE]

[FONT=Courier New][SIZE=3]Error mounting: mount exited with exit code 1: helper failed with:
[mntent]: line 15 in /etc/fstab is bad
[mntent]: line 17 in /etc/fstab is bad
[mntent]: line 18 in /etc/fstab is bad
[mntent]: line 19 in /etc/fstab is bad
[mntent]: line 20 in /etc/fstab is bad; rest of file ignored
mount: can't find /dev/sda5 in /etc/fstab or /etc/mtab[/SIZE][/FONT]

[SIZE=3][FONT=Arial]My quesion to everyone who knows what's going on: is there a quick way to solve this issue, so I could simply automount all partitions when booting Linux, and how can I create other ext4 partitions on unallocated space that I still have on 2 hd's without the burden that access is denied because root is the owner and not me?! :mad:

I spent a lot of time tweaking Gnome to suit my needs, and now I got this problem that I can't solve myself unfortunately. I tried many faqs, read other forum entries, but still couldn't find the solution.

It felt like a revelation when I switched back to Linux after spending years tweaking a slow, resource hogging window$ system, I still use it as a second option, but as soon I found a replacement for any task where I still need window$ apps for, chances are big that I switch to Ubuntu only, erasing my Microsh** system, for it is a pleasure working with Linux again, I should have done this earlier, but you know, about 2 years ago I tried an older Ubuntu version that a friend burned on cd-r for me, but it failed to install, probably because there was an error on the cd itself: Grub failed to work, and eventually my window$ was also messed up, and then I lost my appetite of course..... until I tried v9.10 changing my bios settings to boot from another HD just in case it would go wrong again, but this time I don't regret it.

....so if there's anyone who can help me, I would be very grateful and once more relieved. ;)

Awaiting some advice, I greet you all,

M.
[/FONT][/SIZE]

---

### Post by gavinjb on 2010-08-24
Hi,

It looks like the entries in your fstab are incorrect, can you post your fstab (/etc/fstab).

---

### Post by MusicMagic on 2010-08-24
> **gavinjb said:**
> Hi,

It looks like the entries in your fstab are incorrect, can you post your fstab (/etc/fstab).

Okay, here it is (attached), if you can perhaps see the errors in it? for it is read-only and in ancient linux versions I ran servers for use as an intranet and a gateway to internet for other windows98 and NT 4 workstation systems attached to it in network. So no need for a multiboot, I used SUSE 6.0 for it and went well. But that's already a long time ago, and I was root myself, I don't really understand why Ubuntu disables the root-account by default so you can only use sudo commands in a terminal to execute root functions, but am not familiar with it. Looks a bit like UAC behaviour in Vista or W7 where the admin account is also disabled by default after install.
The old-fashioned ./shutdown -halt 0 or shutdown -R 0 is now suddenly "sudo reboot" ..... looks easier but i'm used to do it otherwise, and if I want to have plain root access in Ubuntu it asks a password that is not mine, so it isn't allowed i guess..... but I must admit I focussed myself primary on tweaking my Gnome desktop, not really concerned about terminal issues, or troubleshooting in command prompt (Bash shell).

Anyway, I just took a look at fstab, looks like one big mess after I tried to create ext4 partitions that could only accessed by root, thus deleted them afterwards, for they're useless. And my main goal was trying to automount everything when booting, so I don't have to mount drives manually anymore. It would be a lot more convenient so I could leave my media files on ntfs drives and creating symbolic links on my desktop for example to those folders. 
What I also don't really understand is, that even if I make extra linux partitions, they are standard also unmounted. Wasn't the case in SUSE and other distro's I used before (slackware, red hat, even though red hat was a plain disaster, i don't like it).

Had to put it in an archive so it could be accepted as a file-attach here.

I must admit that after all those years I feel often like a novice again.

Thx in advance for your help ;)

M.

---

### Post by gavinjb on 2010-08-24
Hi,

My first thought would be to Comment out all the ntfs partitions and then make sure you have the ext4 partitions created in /media and I would also try removing the spaces from the folder names as this could be causing confusion so I would have /media/LinuxA instead of /media/Linux A...

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc             proc         defaults               0  0  
# / was on /dev/sdb6 during installation
UUID=996f3351-da61-47e0-8488-48db819fbab4  /                 ext4         errors=remount-ro      0  1  
# swap was on /dev/sdb7 during installation
UUID=2e9248a0-7b51-4622-bcf5-9c0db36a396a  none              swap         sw                     0  0  
/dev/scd0                                  /media/cdrom0     udf,iso9660  user,noauto,exec,utf8  0  0  
#/dev/sdc1                                  /media/Backup     ntfs         nls=iso8859-1,noauto   0  0  
/dev/sdb1                                  /media/LinuxA    ext4         defaults               0  0  
#/dev/sdb5                                  /media/Downloads  ntfs         nls=iso8859-1,noauto   0  0  
#/dev/sda5                                  /media/Media 1    ntfs         nls=iso8859-1          0  0  
/dev/sda9                                  /media/LinuxB    ext4         defaults               0  0  
#/dev/sda6                                  /media/Media 2    ntfs         nls=iso8859-1          0  0  
#/dev/sda7                                  /media/Media 3    ntfs         nls=iso8859-1          0  0  
/dev/sdb1                                  /media/sdb1       ext4         noauto                 0  0  
#/dev/sda5                                  /media/sda5       ntfs         nls=iso8859-1,noauto   0  0  
#/dev/sda6                                  /media/sda6       ntfs         nls=iso8859-1,noauto   0  0  
#/dev/sda7                                  /media/sda7       ntfs         nls=iso8859-1,noauto   0  0  
#/dev/sda8                                  /media/sda8       ntfs         nls=iso8859-1,noauto   0  0  
/dev/sda9                                  /media/sda9       ext4         noauto                 0  0  

```

Here is the fstab from my test Linux setup
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb1       /               ext4    errors=remount-ro 0       1
/dev/sdb6	/media/MyData	ext4	errors=remount-ro 0	1
# swap was on /dev/sdb5 during installation
UUID=f9726390-0b40-42ee-93cf-983daa9063c2 none            swap    sw              0       0

```

As for your question about sudo you can enable su in Ubuntu, I can't remember how, but if you google it you should find the answer, I would never though login as root in Linux though as it leaves your machine potentially open for anything to be done.

Also if you prefer using su compared to sudo you can run sudo -i in a console and from then on (until you type exit or close the console) you have admin rights, but again for security (and to make sure I dont accidentally break something) I prefer sudo and then command.




Gavin,

---

### Post by MusicMagic on 2010-08-24
Hi Gavin,

> **gavinjb said:**
> Hi,

My first thought would be to Comment out all the ntfs partitions and then make sure you have the ext4 partitions created in /media and I would also try removing the spaces from the folder names as this could be causing confusion so I would have /media/LinuxA instead of /media/Linux A...

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc             proc         defaults               0  0  
# / was on /dev/sdb6 during installation
UUID=996f3351-da61-47e0-8488-48db819fbab4  /                 ext4         errors=remount-ro      0  1  
# swap was on /dev/sdb7 during installation
UUID=2e9248a0-7b51-4622-bcf5-9c0db36a396a  none              swap         sw                     0  0  
/dev/scd0                                  /media/cdrom0     udf,iso9660  user,noauto,exec,utf8  0  0  
#/dev/sdc1                                  /media/Backup     ntfs         nls=iso8859-1,noauto   0  0  
/dev/sdb1                                  /media/LinuxA    ext4         defaults               0  0  
#/dev/sdb5                                  /media/Downloads  ntfs         nls=iso8859-1,noauto   0  0  
#/dev/sda5                                  /media/Media 1    ntfs         nls=iso8859-1          0  0  
/dev/sda9                                  /media/LinuxB    ext4         defaults               0  0  
#/dev/sda6                                  /media/Media 2    ntfs         nls=iso8859-1          0  0  
#/dev/sda7                                  /media/Media 3    ntfs         nls=iso8859-1          0  0  
/dev/sdb1                                  /media/sdb1       ext4         noauto                 0  0  
#/dev/sda5                                  /media/sda5       ntfs         nls=iso8859-1,noauto   0  0  
#/dev/sda6                                  /media/sda6       ntfs         nls=iso8859-1,noauto   0  0  
#/dev/sda7                                  /media/sda7       ntfs         nls=iso8859-1,noauto   0  0  
#/dev/sda8                                  /media/sda8       ntfs         nls=iso8859-1,noauto   0  0  
/dev/sda9                                  /media/sda9       ext4         noauto                 0  0  

```Here is the fstab from my test Linux setup
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb1       /               ext4    errors=remount-ro 0       1
/dev/sdb6    /media/MyData    ext4    errors=remount-ro 0    1
# swap was on /dev/sdb5 during installation
UUID=f9726390-0b40-42ee-93cf-983daa9063c2 none            swap    sw              0       0

```As for your question about sudo you can enable su in Ubuntu, I can't remember how, but if you google it you should find the answer, I would never though login as root in Linux though as it leaves your machine potentially open for anything to be done.

Also if you prefer using su compared to sudo you can run sudo -i in a console and from then on (until you type exit or close the console) you have admin rights, but again for security (and to make sure I dont accidentally break something) I prefer sudo and then command.


Gavin,

Thanks a lot, you brought me to some good ideas, I remade a test ext4-partition LinuxA as you told, and tried to automount it the same way as / is automounted, and commented out all other ntfs drives.
Result: no errors anymore at login (splashscreen free from pollution) and partition LinuxA automounted and the owner is my user account now, not root.
For the rest my other NTFS partitions are again fully accessible, but I have to mount them manually or if I use Filemanager in Gnome ( "Bestandsverkenner" for I use Gnome in Dutch language) I can easilly access them from the left pane by clicking on these drives, so access isn't denied anymore.

This is what I did in fact:

I used the Gnome-function "Terminal as root", went to /etc and typed "gedit fstab" what made it accessible, not read only anymore (I should have known it that I can edit that file this way, but nevermind, we all aren't perfect, right?).
I currently solved it as followed:

```


# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc             proc         defaults               0  0  
# / was on /dev/sdb6 during installation
UUID=996f3351-da61-47e0-8488-48db819fbab4  /                 ext4         errors=remount-ro      0  1  
# swap was on /dev/sdb7 during installation
UUID=2e9248a0-7b51-4622-bcf5-9c0db36a396a  none              swap         sw                     0  0  
/dev/scd0                                  /media/cdrom0     udf,iso9660  user,noauto,exec,utf8  0  0  
#/dev/sdc1                                  /media/Backup     ntfs         nls=iso8859-1,noauto   0  0  
/dev/sdb1                                  /media/LinuxA     ext4         errors=remount-ro       0  1  
#/dev/sdb5                                  /media/Downloads  ntfs         nls=iso8859-1,noauto   0  0  
#/dev/sda5                                  /media/Media 1    ntfs         nls=iso8859-1          0  0  
#/dev/sda9                                  /media/Linux B    ext4         defaults               0  0  
#/dev/sda6                                  /media/Media 2    ntfs         nls=iso8859-1          0  0  
#/dev/sda7                                  /media/Media 3    ntfs         nls=iso8859-1          0  0  
#/dev/sdb1                                  /media/sdb1       ext4         noauto                 0  0  
#/dev/sda5                                  /media/sda5       ntfs         nls=iso8859-1,noauto   0  0  
#/dev/sda6                                  /media/sda6       ntfs         nls=iso8859-1,noauto   0  0  
#/dev/sda7                                  /media/sda7       ntfs         nls=iso8859-1,noauto   0  0  
#/dev/sda8                                  /media/sda8       ntfs         nls=iso8859-1,noauto   0  0  
#/dev/sda9                                  /media/sda9       ext4         noauto                 0  0 


```The option " errors=remount-ro       0  1 " to automount my new made ext4 partition seems to work, and what I think, is that all following code at the bottom of fstab is rather obsolete code that isn't necessary.

```


#/dev/sdb1                                  /media/sdb1       ext4         noauto                 0  0  
#/dev/sda5                                  /media/sda5       ntfs         nls=iso8859-1,noauto   0  0  
#/dev/sda6                                  /media/sda6       ntfs         nls=iso8859-1,noauto   0  0  
#/dev/sda7                                  /media/sda7       ntfs         nls=iso8859-1,noauto   0  0  
#/dev/sda8                                  /media/sda8       ntfs         nls=iso8859-1,noauto   0  0  
#/dev/sda9                                  /media/sda9       ext4         noauto                 0  0 


```I didn't make a second ext4 partition yet, for I wanted to test this out first.
Now, all my NTFS partitions are back accessible by file manager or by manually mounting them, it should be possible to automount them, though? What would you recommend to accomplish this?

But thanks! Your advice helped a lot: got no errors anymore and the desired result is great, it would be just more convenient to be able to automount ALL partitions.... :D

Greetings,

Mick.

---

### Post by cAlpha on 2010-08-24
> **MusicMagic said:**
> Hi Gavin,



Thanks a lot, you brought me to some good ideas, I remade a test ext4-partition LinuxA as you told, and tried to automount it the same way as / is automounted, and commented out all other ntfs drives.
Result: no errors anymore at login (splashscreen free from pollution) and partition LinuxA automounted and the owner is my user account now, not root.
For the rest my other NTFS partitions are again fully accessible, but I have to mount them manually or if I use Filemanager in Gnome ( "Bestandsverkenner" for I use Gnome in Dutch language) I can easilly access them from the left pane by clicking on these drives, so access isn't denied anymore.

This is what I did in fact:

I used the Gnome-function "Terminal as root", went to /etc and typed "gedit fstab" what made it accessible, not read only anymore (I should have known it that I can edit that file this way, but nevermind, we all aren't perfect, right?).
I currently solved it as followed:

```


# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc             proc         defaults               0  0  
# / was on /dev/sdb6 during installation
UUID=996f3351-da61-47e0-8488-48db819fbab4  /                 ext4         errors=remount-ro      0  1  
# swap was on /dev/sdb7 during installation
UUID=2e9248a0-7b51-4622-bcf5-9c0db36a396a  none              swap         sw                     0  0  
/dev/scd0                                  /media/cdrom0     udf,iso9660  user,noauto,exec,utf8  0  0  
#/dev/sdc1                                  /media/Backup     ntfs         nls=iso8859-1,noauto   0  0  
/dev/sdb1                                  /media/LinuxA     ext4         errors=remount-ro       0  1  
#/dev/sdb5                                  /media/Downloads  ntfs         nls=iso8859-1,noauto   0  0  
#/dev/sda5                                  /media/Media 1    ntfs         nls=iso8859-1          0  0  
#/dev/sda9                                  /media/Linux B    ext4         defaults               0  0  
#/dev/sda6                                  /media/Media 2    ntfs         nls=iso8859-1          0  0  
#/dev/sda7                                  /media/Media 3    ntfs         nls=iso8859-1          0  0  
#/dev/sdb1                                  /media/sdb1       ext4         noauto                 0  0  
#/dev/sda5                                  /media/sda5       ntfs         nls=iso8859-1,noauto   0  0  
#/dev/sda6                                  /media/sda6       ntfs         nls=iso8859-1,noauto   0  0  
#/dev/sda7                                  /media/sda7       ntfs         nls=iso8859-1,noauto   0  0  
#/dev/sda8                                  /media/sda8       ntfs         nls=iso8859-1,noauto   0  0  
#/dev/sda9                                  /media/sda9       ext4         noauto                 0  0 


```The option " errors=remount-ro       0  1 " to automount my new made ext4 partition seems to work, and what I think, is that all following code at the bottom of fstab is rather obsolete code that isn't necessary.

```


#/dev/sdb1                                  /media/sdb1       ext4         noauto                 0  0  
#/dev/sda5                                  /media/sda5       ntfs         nls=iso8859-1,noauto   0  0  
#/dev/sda6                                  /media/sda6       ntfs         nls=iso8859-1,noauto   0  0  
#/dev/sda7                                  /media/sda7       ntfs         nls=iso8859-1,noauto   0  0  
#/dev/sda8                                  /media/sda8       ntfs         nls=iso8859-1,noauto   0  0  
#/dev/sda9                                  /media/sda9       ext4         noauto                 0  0 


```I didn't make a second ext4 partition yet, for I wanted to test this out first.
Now, all my NTFS partitions are back accessible by file manager or by manually mounting them, it should be possible to automount them, though? What would you recommend to accomplish this?

But thanks! Your advice helped a lot: got no errors anymore and the desired result is great, it would be just more convenient to be able to automount ALL partitions.... :D

Greetings,

Mick.

Two things:
(1)  I could be missing something, but why are you specifying options "nls=iso8859-1" and "noauto" for each of your NTFS entires?  Seems to me, "noauto" could certainly be what's preventing the partitions from being mounted automatically...

(2)  Also, I had the same problem regarding mounting a drive with a space.  You need to use the octal value of a space (040) to get it working (eg, /media/File\040Share)

See if using the following, replacing your created drive names and respective disk for mine, doesn't get them mounting automatically:  
  /dev/sda5 /media/File\040Share ntfs defaults 0 0

---

### Post by brr872002 on 2010-08-24
edit fstab add defaults for auto mount
/dev/sda6  /media/sda6    ntfs-3g  defaults  0 0

---

### Post by redmk2 on 2010-08-25
Double post.  Sorry :redface:

---

### Post by redmk2 on 2010-08-25
Just a note in passing.  You might want to consider using UUID's instead of the older */dev/sd**x ***method.  Modern Linux distros do not always enumerate the partitions in the same order every time the host is booted.  This means that the /dev/sd**x** device reference can (will) change when drives are added or subtracted from the system.  just adding a USB pen drive can upset the order.

This is what the below (highlighted in red) is referring to.  Learn how to ID drives by UUID for long term stability.  

The command to see the UUID of the various partitions is```
sudo blkid
```

The subject of UUID's  is also covered [**_here_**]("https://help.ubuntu.com/community/UsingUUID").


```

# /etc/fstab: static file system information.
#
[B][COLOR="Red"]# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).[/COLOR][/B]
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=b00ff2b7-20cd-4382-a47d-33ab5fd0a92c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=0ec8add1-6175-42b5-95fc-faa236663ee1 /home           ext3    relatime        0       2
# /dev/sda4
UUID=5ee83ac2-45ba-40bd-b09c-23be48ba7ccc /smb            ext3    relatime        0       2
# /dev/sda2
UUID=a91da982-91ff-4685-810f-eb6850bf1fa1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

---

### Post by MusicMagic on 2010-08-25
> **cAlpha said:**
> Two things:
(1)  I could be missing something, but why are you specifying options "nls=iso8859-1" and "noauto" for each of your NTFS entires?  Seems to me, "noauto" could certainly be what's preventing the partitions from being mounted automatically...

(2)  Also, I had the same problem regarding mounting a drive with a space.  You need to use the octal value of a space (040) to get it working (eg, /media/File\040Share)

See if using the following, replacing your created drive names and respective disk for mine, doesn't get them mounting automatically:  
  /dev/sda5 /media/File\040Share ntfs defaults 0 0

(1) Well, what actually happened is, that I tried to customise things (so I could automount) using an utility I found in Ubuntu Software Center: "**Storage Device Manager**" (allows full customization of hard disk mountpoints without manually access to fstab.....) but it seemed a seriously buggy application that messed up a lot so I uninstalled it, and tried to restore the damage done as much as possible using the common drive and media utilities standard included in the 10.04 LTS distro. Which I couldn't. So I tried the "noauto" function thereafter to get rid of error messages while booting, using the front-end of drive utilities, not editing fstab itself, but if just messed up even more the content of my fstab file. My experience is that many things that I've found in the Ubuntu Software Center are from suspicious quality: nasty bugs etc..... I think it's better not to go there if you need something useful :(  (at least, that is my vision).
Over 32.000 applications, all free and open source? It's hard to find quality into such a massive library!

(2) Yes, you got a point, my previous experiences with Linux, are that it wasn't possible to use spaces into filenames and in fact a partition is mounted as a directory ... you start with / but all things in e.g. /usr can as well be on another hd or partition that is mounted this way. When I installed Ubuntu I was initially surprised that it could deal with filenames with spaces in it. In fact I begin to think that it's not really true that spaces are fully supported. Another mistake. I haven't thought about the use of that octal value (040) - still got a lot to learn and recognise again.

Last years I mostly maintained webservers (apache, the windows version, that works in practice not very different) and built my own websites from scratch in a txt-editor (notepad), for I don't like wysiwyg crap, and I always replaced spaces with %20 in my codes for an url, hyperlinks etc can't handle spaces either, I was perhaps too many busy doing javascript and html coding, and with security matters in windows environments that I lost many old-fashioned knowledge that is in fact still valid, I think that Im starting to have a better idea about how Linux distros are evolved during the past decade: on the outside there is a lot changed, instant GUI install without the need to manually install X-windows and old-fasioned YAST-installations, manual kernel compiling and other installations is now replaced by an update manager that does everything automatically for you...... it almost seemed like times of pure manual installs and compiling binaries yourself from just source codes are completely over.... I don't think that's totally true, it all looks very much userfriendly now at first sight, but there is still a lot of work to be done to make Linux fit for the common Average Joe who still gets a panic attack whenever something goes wrong that has to be solved in a shell.

I apologise for my opinion above, it doesn't make it less challenging for me to keep on using Ubuntu, for all other OS including MacOsx and Windows cannot beat a decent finetuned and tweaked linux system: faster, less resources needed - optimal performance with minimal hardware and ram requirements, try to tell this to the Redmond Mothership of Empy Wallet victims ;) .... but to get back **on-topic now**:

Ubuntu just took over the original drive names as I created and use them in Windows. Thus, if I'm right, to avoid any future issues, it's always best make sure to boot back to Windows, changing all drive names with spaces into other suitable names so I could better work with them in Linux? It would make things easier in theory, but then I just wonder if I don't get into troubles when Ubuntu doesn't automatically recognise drive name changes made in another OS.

Note:

Still got other things to solve too, like soundcard incompatibilities, and issues with properly configuring my Nvidia GeForce videocard but these things can wait for now, still got Windows when I want to listen, edit or making music, no hurry. Those are obviously driver issues, and I know from experience that configuring hardware the right way by finding the correct drivers (if they exist) can be quite tough.
But for example: compare the use of Firefox in Linux with Firefox in Windows and you will notice why I prefer to work in Gnome, thus currently I boot Windows just once in a few days whenever really necessary. :)

I'll let you know if it works when I try things the way you and others here suggest to solve this issue properly. Thx for the advice in advance,

Mick

---

