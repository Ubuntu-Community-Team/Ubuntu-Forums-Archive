---
title: "Booting Ubuntu from a work computer"
date: 2009-10-05
forum: General Help
---

### Post by mjp29 on 2009-10-05
I brought my live cd to work to boot it to show some coworkers what it was.

Is it possible that the computers at work are set up in such a way to prevent booting into anything other than Windows and Novell Network.

I did try once to hold down "c" key while booting and the computer attempted to access the floppy drive to search for something and reported back it couldn't find what it was looking for.  But I did not hear or see any lights activate in the cd drive.

---

### Post by blur xc on 2009-10-05
> **mjp29 said:**
> I brought my live cd to work to boot it to show some coworkers what it was.

Is it possible that the computers at work are set up in such a way to prevent booting into anything other than Windows and Novell Network.

I did try once to hold down "c" key while booting and the computer attempted to access the floppy drive to search for something and reported back it couldn't find what it was looking for.  But I did not hear or see any lights activate in the cd drive.

Dunno about your "c" key, but maybe the bios is set to only boot off of the primary hdd, and not off of anything else...

BM

---

### Post by undecim on 2009-10-05
If it's accessing the floppy drive, you can use a GRUB floppy to boot into a thumb drive (i don't think grub boots cds.). You can create the thumb drive with the "USB Startup Disk Creator" from the Administration menu.

To make the floppy, you need access to linux computer with a floppy drive to make the grub floppy. (It can be done on windows too, but I wouldn't know how.) I found an image download here: [http://gazonk.org/~eloj/files/grubbootimage.zip](http://gazonk.org/~eloj/files/grubbootimage.zip)

extract the zip file, and use this command to write the image to the floppy:
```
sudo dd if=/path/to/disk/image of=/dev/fd0
```
where "/path/to/disk/image" is the path the image you extracted.

Then, when you boot the disk (you will want to test this at home first) you will get a grub prompt. Type the following lines: (NOTE: The drive will not always be "(hd1,0)" this refers to the second hard drive's first partition, so you may need to change this)
```
rootnoverify (hd1,0)
chainloader +1
boot
```

---

### Post by steveneddy on 2009-10-05
If your company has the PC's set up not to boot from a CD then take your laptop to work or make some screenshots and post them on Plaxo and show them the OS in this manner.

I'm not saying you will, but you may lose your position of employment at said company if someone witnesses you trying to boot up "a Linux virus".

Play it safe and don't try this on work PC's. They aren't yours and you do not have permission to muck around in the BIOS or any other parts of the machine unless directed to do so by someone in an administrative position.

On a personal note:
If you didn't know before this thread that a BIOS change may solve the issue, then you really don't need to be messing around with work PC's.
/personal.opinion

Go ask your boss and get his/her permission to "show and tell" your new toy.

---

### Post by blur xc on 2009-10-05
> **steveneddy said:**
>  I'm not saying you will, but you may lose your position of employment at said company if someone witnesses you trying to boot up "a Linux virus".

Play it safe and don't try this on work PC's. They aren't yours and you do not have permission to muck around in the BIOS or any other parts of the machine unless directed to do so by someone in an administrative position.


Totally depends on the situation.  On a bigger company, it might be an issue, but for example in a small company, each employee might be their own IT tech.  I'm in charge of maintaining and running my work laptop, which includes installing whatever software I want on it.  My boss may no know that I installed VBox w/ Crunchbang linux, and some other os's running inside of it, but I know he won't fire me for it.  I might bet a few words about how I'm spending my time at work though...

BM

---

### Post by SonniDaze on 2009-10-05
I work in a manufacturing facility as an IT person.  If I caught someone loading a linux operating system (even a live cd) on a machine I would have to report it.  My companies computer/internet policies are severe, One instance and you can be terminated.  Play it safe - Make a few copies of the cd and give them to your coworkers to play around with it at home.

---

