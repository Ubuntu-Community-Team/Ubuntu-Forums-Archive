---
title: "RSYNCing /home with ownership problems"
date: 2009-10-19
forum: General Help
---

### Post by Rehd on 2009-10-19
Hei,

I am quite new to Linux/Ubuntu and very happy about it. Started just recently to write my own scripts.

I found rsync quite straightforward and wrote a little script to mirror my /home directory to a 16GB-USB-Flash-drive.

Somehow things getting more complicated without me changing anything.

1) In the beginning (maybe when Hardy came last year) I started with:
```
rsync -au --exclude '.*' --exclude '*~' /home/ME/ /media/USBdisk/
rsync -au --exclude '.*' --exclude '*~' /media/USBdisk/ /home/ME/
sync;sync;sync
umount /dev/sdc1/
```
not very elegant, but it worked! It did eject the USB drive.


2) Then after a while (some update?) umount did not work anymore?!
I tried it in a shell and I got an error with permissions; but I swear it worked!

So I just deleted
```
umount /dev/sdc1/
```

3) Then suddenly I got error messages after login, complaining about

> User's $home/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permission. User's $home directory must be owned by user and not writable by other user's.

It took me some weeks to find out that suddenly my rsync script messed up those permissions, though I do not touch the .dmrc file.

So I added

```
chmod 644 /home/reinhard/.dmrc
chmod o-w /home/reinhard/
```

4) Now I am trying Koala Beta (Xubuntu amd64) and I LOVE it a lot. This is really good work and it is my favorite of all the great Ubuntus so far.

But the rsync script gets even more into trouble:

When I use it, everything goes fine, BUT it takes ages on error messages complaining for each and every file and directory:
```
rsync: chgrp "/media/disk/*whatever*" failed: Operation not permitted
```

ls -l /media shows
```
drwxr-xr-x 18 rforge root 8192 2009-10-19 13:09 disk
```for the USB-flashdrive.

I tried to change the group to rforge (my username) to no avail.


=> As anyone who uses rsync can see: I just want to mirror the usb-disc and my home directory. I would really appreciate any useful thoughts on this. And it would be great if someone knew a way to eject the disk form the script!

Best regards,
Reinhard

---

### Post by Giblet5 on 2009-10-19
To assign the correct permissions to rsync'ed files use the -p option.

If those permissions are something other than your UID/GID however, you will have to do it as the superuser.

```
sudo rsync -aurpt .....
```

Will preserve permissions, directory tree, and file timestamps.

---

### Post by Giblet5 on 2009-10-19
PS: It is inevitable that you'll wind up with files and directories under your $HOME that do not belong to you. You can fix that via ```
sudo chown -R `username`:`username` $HOME
```

---

### Post by Rehd on 2009-10-20
> **Giblet5 said:**
> To assign the correct permissions to rsync'ed files use the -p option.

If those permissions are something other than your UID/GID however, you will have to do it as the superuser.

```
sudo rsync -aurpt .....
```

Will preserve permissions, directory tree, and file timestamps.

Thanks a lot for fast answer.

The point is that rsync DOES try to change the group on the USB-disk and gets rejected to do so, which results in a flood of errors "chgrp not permitted".

The GID of the automaticly mounted USB-drive is "root" and I am not allowed to change this - not even as root.

Any suggestions?

---

### Post by Giblet5 on 2009-10-20
> **Rehd said:**
> Thanks a lot for fast answer.

The point is that rsync DOES try to change the group on the USB-disk and gets rejected to do so, which results in a flood of errors "chgrp not permitted".

The GID of the automaticly mounted USB-drive is "root" and I am not allowed to change this - not even as root.

Any suggestions?


Don't even try to rsync with perms to a NTFS or VFAT filesystem! Those filesystems have no understanding of Unix permissions and ownerships.

If you absolutely must back up to a lameoid filesystem, then use the tar command:

```
sudo tar -cjf /media/WinFiles/home-backup.tar.bz2 /home
```

and to restore:

```
cd /
sudo tar -xjf /media/WinFiles/home-backup.tar.bz2
```

Tar will preserve permissions and timestamps within the archive, then store the archive anywhere you can write-to in heavily-compressed form.

To list, with extreme detail, the contents of the backup: ```
tar -tvjf /media/WinFiles/home-backup.tar.bz2
```

---

### Post by Giblet5 on 2009-10-20
Backing up Linux onto a windows filesystem is like putting your money in a safe, then putting the safe in the middle of a busy street, in a very bad neighborhood: right idea, poor implementation.

If you must backup remote linux files onto a local USB drive that's formatted for Windows, and you want to do so in a single step:

```
ssh remotehostname tar cjf - /remotedirname | bzip2 -c > /media/WinFiles/remotehostname-backup.tar.bz2
```

Or, you can format the USB drive for ext3/ext4 and use rsync.

---

### Post by Rehd on 2009-10-20
> **Giblet5 said:**
> Don't even try to rsync with perms to a NTFS or VFAT filesystem! Those filesystems have no understanding of Unix permissions and ownerships.

Thank you again for instant help!

I do understand that FAT32 does not support UID/GID, but: I did work before as I mentioned!

The point is, that I am using Xubuntu Koala on my Thinkpad (I accidentially even nuked my employees XP partition with a Kamikaze newbee 'sudo rm -r' mistake)
and
XP on my Work-PC.

I am switching between both, so my real /home is the USB-disk which I switch between many Workstations in several locations (mostly XP).

My workhorse of choice is my Xubuntu/Emacs/X61-thinkpad since November last year and this is beyond anything I could dream of.

So it is not really a backup, but sharing the USB-disk between XP and Xubuntu with a kind of backup on both the Ubuntu /home and on a XP-Dell (using cwRsync).

Believe it or not it did work, without a fuzz.

```
rsync -au $HOME/ /media/USBdisk/
```
in Ubuntu 
and
```
Technical\cwRsync\bin\rsync -au --exclude '.*' --exclude '*~' --exclude 'Music/' "/cygdrive/e/" "/cygdrive/h/DATA/home/"
```
with cwRsync in XP Professional.

Suggestions? It did work in November through September. Maybe I had the USBdisk formated as NTFS. I should give this a try.

---

### Post by Giblet5 on 2009-10-20
> **Rehd said:**
> Thank you again for instant help!

I do understand that FAT32 does not support UID/GID, but: I did work before as I mentioned!

The point is, that I am using Xubuntu Koala on my Thinkpad (I accidentially even nuked my employees XP partition with a Kamikaze newbee 'sudo rm -r' mistake)
and
XP on my Work-PC.

I am switching between both, so my real /home is the USB-disk which I switch between many Workstations in several locations (mostly XP).

My workhorse of choice is my Xubuntu/Emacs/X61-thinkpad since November last year and this is beyond anything I could dream of.

So it is not really a backup, but sharing the USB-disk between XP and Xubuntu with a kind of backup on both the Ubuntu /home and on a XP-Dell (using cwRsync).

Believe it or not it did work, without a fuzz.

```
rsync -au $HOME/ /media/USBdisk/
```
in Ubuntu 
and
```
Technical\cwRsync\bin\rsync -au --exclude '.*' --exclude '*~' --exclude 'Music/' "/cygdrive/e/" "/cygdrive/h/DATA/home/"
```
with cwRsync in XP Professional.

Suggestions? It did work in November through September. Maybe I had the USBdisk formated as NTFS. I should give this a try.


Of course it worked.

```
rsync -au ...
```

doesn't try to preserve permissions and ownership (-p), timestamps (-t), or directory trees (-r).

Permissions will only work on ext2, ext3, or ext4 filesystems.

Full timestamps (st_ctime, st_mtime, and st_atime) will be truncated to st_mtime on NTFS or VFAT.

This is a very very weird thing you're doing, although creative, but I have to warn you that disaster is almost inevitable.

I hope you're truecrypting that USB drive...

---

### Post by Rehd on 2009-10-20
> **Giblet5 said:**
> Of course it worked.

```
rsync -au ...
```

doesn't try to preserve permissions and ownership (-p), timestamps (-t), or directory trees (-r).


uhu.. that would void the meaning of rsync -a since it is looking for timestamps as far as I understood... so it is weird that it worked at all before.. and now it is weird that it does not work anymore because of a GID conflict?!?

> This is a very very weird thing you're doing, although creative, but I have to warn you that disaster is almost inevitable.

Yes, I am getting aware in the course of this conversation, that it was quite risky, what I was doing, so I might leave this road for another approach.

It was so stunning easy and nice: with 2 lines of naive BASH everything worked as desired... I could not believe initally

```
I hope you're truecrypting that USB drive...
```
what does this mean?

And thanks a lot for you patience. It definitely helped to clear my thoughts.

---

### Post by Giblet5 on 2009-10-20
> **Rehd said:**
> uhu.. that would void the meaning of rsync -a since it is looking for timestamps as far as I understood... so it is weird that it worked at all before.. and now it is weird that it does not work anymore because of a GID conflict?!?

-a *uses* the timestamps to determine what to copy. It does not preserve them.



> Yes, I am getting aware in the course of this conversation, that it was quite risky, what I was doing, so I might leave this road for another approach.

It was so stunning easy and nice: with 2 lines of naive BASH everything worked as desired... I could not believe initally

```
I hope you're truecrypting that USB drive...
```
what does this mean?

And thanks a lot for you patience. It definitely helped to clear my thoughts.

Truecrypt is a third-party (free) filesystem encryption tool that is, for all intents and purposes, completely uncrackable by anyone. There's even a way to prevent full access when someone is holding a gun to your head and demanding the password - they won't know that you told a half-truth. It's available for Windows, Linux, and others.

Truecrypt is for people who lug their personal/sensitive data around with them.

---

### Post by QLee on 2009-10-20
[QUOTE=Rehd]
I am quite new to Linux/Ubuntu and very happy about it. Started just recently to write my own scripts.[/QUOTE]

Great, this can be a good way to learn for some people, good luck.

[QUOTE=Rehd]=> As anyone who uses rsync can see: I just want to mirror the usb-disc and my home directory. I would really appreciate any useful thoughts on this. And it would be great if someone knew a way to eject the disk form the script!
[/QUOTE]

I do agree with poster Giblet5 that what you are trying is non-standard, I won't go quite as far as saying "weird" but it might not be the best approach. You might want to look into software that is designed for mirroring a directory, perhaps "unison" or some others that you might find.

Another couple of things I want to mention, you could consider using LABEL or UUID rather than device node to mount and unmount your drive, that could avoid any times when it isn't mounted as /dev/sdc1. I note your script doesn't have a mount command or a test that the drive is mounted, what happens when you forget to mount the drive before the script runs?

You've got lots of good advice and information in this thread, keep at your programing and continue to trace why things you try fail, each time you will become more adept.

---

### Post by Rehd on 2009-10-21
> **QLee said:**
> Great, this can be a good way to learn for some people, good luck.
First of all, thank you guys for all advice and help! And, yes, I am learning a lot this way... and as long as patients lasts I enjoy it a lot.
(edit: of course "... as long as my patience is lasting I am enjoying" and there are well countless *nix-patients like me ...)

> I do agree with poster Giblet5 that what you are trying is non-standard, I won't go quite as far as saying "weird" but it might not be the best approach. You might want to look into software that is designed for mirroring a directory, perhaps "unison" or some others that you might find.

I will install unison asap and try it out. Sitting at work right now, with the firewall blocking everything not beeing IE on port 80 ... Thats one of the reasons my primitive, naive and maybe weird Fat32-USB-disk-mirror-solution is so essential to me..

> Another couple of things I want to mention, you could consider using LABEL or UUID rather than device node to mount and unmount your drive, that could avoid any times when it isn't mounted as /dev/sdc1. I note your script doesn't have a mount command or a test that the drive is mounted, what happens when you forget to mount the drive before the script runs?
I do not know what LABEL or UUIDs are, but I will look it up. Ubuntu mounts the disk always as /media/somename, where "somename" is something like KINGSTON or SONY or whatever and is unique and stable for the different USB-disks I use.. so it is always mounted after inserting and has always the same mountpoint, BUT (as I mentioned before) is always mounted with GID "root" and ```
sudo chgrp -R 'rforge' /media/disk
``` does not work...

> You've got lots of good advice and information in this thread, keep at your programing and continue to trace why things you try fail, each time you will become more adept.
Definitely true... there is no way back to MS. The one big thing I appretiate most with the open source culture is: it is definitely not perfect, sometimes (more often) it is not easy (as life) but I am the one responsible, in charge of my own OS and there is a lot of help and support. Amazing.

---

### Post by egalvan on 2009-10-21
> **Rehd said:**
> First of all, thank you guys for all advice and help! And, yes, I am learning a lot this way... and as long as patients lasts I enjoy it a lot.

You'll find that as long as you want to learn, the patience on this forum will last, and last, and last....

> 
I do not know what LABEL or UUIDs are, but I will look it up. Ubuntu mounts the disk always as /media/somename, where "somename" is something like KINGSTON or SONY or whatever and is unique and stable for the different USB-disks I use.. so it is always mounted after inserting and has always the same mountpoint, BUT (as I mentioned before) is always mounted with GID "root" and ```
sudo chgrp -R 'rforge' /media/disk
``` does not work...

LABEL is *nix for "disk name" under Windows.
KINGSTON or SONY are examples of LABEL.
Windows will show these as the name of the drive.
(*nix-way is all lower case, with no spaces.
Windows-way accepts mixed case, and spaces.
I think *nix-way is easier and neater)

They may or may not be unique...
you may have one or more drives named KINGSTON.

UUID is Universily Unique IDentifier.
Theoretically, these are absolutely unique, never-repeating identification labels.
They are automatically assigned when the partition is created.
If the partition is erased, that UUID disappears, never to be seen again.

Here's a Wiki link

[http://en.wikipedia.org/wiki/Universally_Unique_Identifier](http://en.wikipedia.org/wiki/Universally_Unique_Identifier)

> 
Definitely true... there is no way back to MS. The one big thing I appretiate most with the open source culture is: it is definitely not perfect, sometimes (more often) it is not easy (as life) but I am the one responsible, in charge of my own OS and there is a lot of help and support. Amazing.

It is no more, or less, easy, than Microsoft.
Just different.
You probalbly felt the same sense of "being lost" the first time you used a Microsoft-based machine.

"You press "Start" to stop the machine? What fool thought *that* up?"

---

### Post by Rehd on 2009-10-23
> **QLee said:**
> You might want to look into software that is designed for mirroring a directory, perhaps "unison" or some others that you might find.

Yeah, thanks. That was well what I should use. I will try and recommend
```
sudo aptitude install unison
```
to my fellow Linux-newbee colleges (I could inspire at least one to leave the XP+SPSS road and go Ubuntu+R+Emacs).

---

