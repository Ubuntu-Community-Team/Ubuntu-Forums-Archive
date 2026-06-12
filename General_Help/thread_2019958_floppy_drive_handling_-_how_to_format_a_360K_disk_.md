---
title: "floppy drive handling - how to format a 360K disk in a 1.2M drive?"
date: 2012-07-07
forum: General Help
---

### Post by Ronny Svedman on 2012-07-07
I have 12.04LTS /amd64 installed on a opteron 175/abit AV8 system with 
one 1.44  3 1/2 inch and one 1.2 5 1/4 inch floppies connected to the motherboard controller (it's a VIA something or other, dmesg can be arranged if it's important).

They  work perfectly under NetBSD. In ubuntu, they do show up as /dev/fd0 and fd1, and nautilus shows two drive icons. however when I try to "discover media" the nutilus window sometimes changes the path indication and then hongs, and sometimes just disappears. Also, kfloppy is unable to format any disk, and gives the error: "internal error: device not correctly configured"

When I tried to format with fdformat it turned out I do not have the different devices for various formats (for example /dev/fd0h1440 or /dev/fd1d360 (which I would have liked to use) I have avague recollection it did work back in 8.04 or so, but that was on i386 and different hardware.


Any suggestions?

---

### Post by oldfred on 2012-07-08
Floppy?

Some posted this:

[http://ubuntuforums.org/showthread.php?t=1877488](http://ubuntuforums.org/showthread.php?t=1877488)
Mount floppy from command line - Nautilus often does not work
udisks --mount /dev/fd0
ls /dev/fd*

---

### Post by Ronny Svedman on 2012-07-10
That mounts the floppy and I can read it, but writing does not work, even if I sudo cp xxx.yyy /media/floppy0 it will not write, permission denied. the writeprotect tab is closed, (no hole).

I will boot another OS to verify that the hardware can write (old stuff...) and come back. Leaving the thread unsolved for now.


Also, that only works with 1.44 meg floppies, I have many old 720K disks from my Atari ST days that I want to image for use in Hatari. I can do it with null modem but it takes ages and I would have to get the ST from the basement... I can't believe the attitude in the bug thread that lets the problem go unfixed for three years.

---

### Post by Ronny Svedman on 2012-07-10
Edit: I *can* read and write the floppy via the /media/fd0 link.

---

### Post by Ronny Svedman on 2012-07-10
Found out how to use setfdprm( 8 )
 to set the media size for fdformat, since ubuntu doesn't have the different sized device nodes (fd0H1440 et al ) now my problem is solved. 

Kfloppy still gives the same error though (device not correctly configured), but this is good enough for me for now. Also, once I have mounted a disk once in a drive (with udisks --mount /dev/fd0) , the "detect media"  and "mount" in nautilus starts working for that drive.

---

