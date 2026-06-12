---
title: "Any gddrescue advice?"
date: 2010-11-28
forum: General Help
---

### Post by B-Navigator on 2010-11-28
ok, I'm trying to help my brother who's recently had a serious hard drive failure on his machine.  I have tried one of two other approaches, but it's clear there could be building problems, so I'm looking to try using Gddrescue as a way to hopefully solve everything.
I've read through the advice [Here]("http://ubuntuforums.org/showthread.php?t=1057225"), [Here]("http://linuxers.org/howto/how-recover-data-a-damaged-drive-or-filesystem") and [Here,]("http://ubuntuforums.org/showthread.php?t=308821") but I've generally had more problems caused by failing to ask advice than by asking it.  Plus when I tried checking gnu.org for the manual, my browser couldn't connect.

Ok, it looks like this is a pure terminal operation so hopefully I can map out most of the commands to cut paste format beforehand.  Step one, after booting the system with the drive to recover connected, I'll first need to find it with ```
sudo fdisk -l
```
And also find the target disk for the data output to be saved to.  The disk involved is noticably bigger than my Linux partition.  I do have a NTFS disk on the system with enough room to fit the image, There shouldn't be trouble with that right?  Or would just getting an extra hard drive be less hassle?
Anyways, once I know which drives, I'm assuming this is what I'd need to run:```

ddrescue v /dev/[COLOR="Magenta"](damaged drive)[/COLOR] /dev/[COLOR="Magenta"](targetDrive)[/COLOR]/recovereddata.iso
```
And after the opperation is done, the iso can be mounted and read to see what data could be recovered.

Though, I do have a few other questions, after looking over all the data on gddrescue online.  First off, one of the listed key points of ddrescue is that it can be run multiple times, each time filling in any data that doesn't generate an error on that pass.  And it also has the ability to read backward, in case there's a physical problem that can be bypassed that way.  I can't tell if there's any any problems with combining the two approaches from the online documentation.  Also, will specifying a logfile help?  While I can't seem to log onto the source documentation, I do have a lit of commands, including -l logfile: name of a file to log errors and summary to (def="").

Basically I'm just trying to make sure I've got the right proceedure figured out before doing something that could mess things up.
Thanks for any aid in advance.

---

### Post by dcstar on 2010-11-28
> **B-Navigator said:**
> 
.........
Basically I'm just trying to make sure I've got the right proceedure figured out before doing something that could mess things up.
Thanks for any aid in advance.

There is **nothing** to "mess up", all you are doing is trying to read from a drive and write a file - you can do this as many times as you need to.

Stop fussing over things that aren't real and just try to recover the data.

---

### Post by B-Navigator on 2010-11-28
> **dcstar said:**
> There is **nothing** to "mess up", all you are doing is trying to read from a drive and write a file - you can do this as many times as you need to.

Stop fussing over things that aren't real and just try to recover the data.

Well I don't know what's causing the problems with the drive, so it's possible every time it's powered up could be the last time it works. Which is why I'm trying to make sure every use counts.

Thus I'm doing a dry run with a different disk to work out the kinks.
So far, Kink #1, identifying the disk where I've got some space cleared out on, since I have more than one identically sized disk and only one has been emptied enough to fit the iso.  Using the Storage Device Manager and checking which drives were mounted identified the letter, though I'm sure there's an easier way.
More seriously, on trying the test recovery from the still good disk, here's the code and the response:```
brendan@Brendan-Linux:~$ ddrescue v /dev/sdd /dev/sdc/TestRec.iso
ddrescue: cannot open input file: No such file or directory

```
Any thoughts on what's wrong?

---

### Post by B-Navigator on 2010-11-28
Ok, error halfway solved, forgot the - in the syntax.

Adding it prompted: ```
brendan@Brendan-Linux:~$ ddrescue -v /dev/sdd /dev/sdc/TestRec.iso
ddrescue: cannot open input file: Permission denied

```
and then 
```
brendan@Brendan-Linux:~$ sudo ddrescue -v /dev/sdd /dev/sdc/TestRec.iso
ddrescue: cannot open output file: Not a directory

```
Currently clearing out my drive since the Iso option doesn't seem to be working so well.

---

### Post by dcstar on 2010-11-30
> **B-Navigator said:**
> 
.........
and then 
```
brendan@Brendan-Linux:~$ sudo ddrescue -v /dev/sdd **/dev/sdc/TestRec.iso**
ddrescue: cannot open output file: **Not a directory**

```
Currently clearing out my drive since the Iso option doesn't seem to be working so well.

Devices do **not** have files or folders, mounted filesystems have files and folders.

---

