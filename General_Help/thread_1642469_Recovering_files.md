---
title: "Recovering files?"
date: 2010-12-10
forum: General Help
---

### Post by flooj on 2010-12-10
I posted something on here a few weeks ago, and I didn't get any responses.  To sum it up, my ubuntu broke.  I dual boot with Vista, and select the ubuntu at boot up, and it directs me to a grub command prompt screen.
I'm stuck on there, and I have no idea what to do to get back into my ubuntu.
 
So, since I can't get in, is there a way to recover the data off the ubuntu partition of my hard drive.  I looked at the hard drive through Windows and it couldn't find the partition that was part of ubuntu.  Any ideas on how to recover the files?  I have important files on Ubuntu that I really want to recover.  
Help?

---

### Post by iponeverything on 2010-12-10
boot using the live CD or USB stick to access your data.

---

### Post by tredegar on 2010-12-10
You cannot even get to the grub prompt and boot to rescue mode?

Boot from a live CD. Do NOT choose or click install!
Mount your linux partitions. Your files should be there
Plug in a USB disk.
Copy your personal files to safety.
Unmount the USB disk, check your files are all there (I prefer to have an ext3/4 USB disk for this sort of thing)

Reinstall.

Maybe someone has a better idea, so be patient.

---

### Post by azertyh on 2010-12-10
hello,
read the doc [https://help.ubuntu.com/community/LiveCdRecovery](https://help.ubuntu.com/community/LiveCdRecovery)

---

### Post by owiknowi on 2010-12-10
This tip came from mlentink on an other thread (accessing Linux partition from ms wx):

Quote
"you could use [www.fs-driver.org](www.fs-driver.org) works fine"
End quote

Either way - live CD or fore mentioned driver - should enable you to backup your files from /home/username to an external disk.

Tip: backup your personal files on a daily base to an external disk.

---

### Post by dtfinch on 2010-12-10
Could try [http://sourceforge.net/projects/ext2read/](http://sourceforge.net/projects/ext2read/) to read the files from Windows, though I haven't used it myself.

---

### Post by flooj on 2010-12-11
> **tredegar said:**
> You cannot even get to the grub prompt and boot to rescue mode?

Boot from a live CD. Do NOT choose or click install!
Mount your linux partitions. Your files should be there
Plug in a USB disk.
Copy your personal files to safety.
Unmount the USB disk, check your files are all there (I prefer to have an ext3/4 USB disk for this sort of thing)

Reinstall.

Maybe someone has a better idea, so be patient.


To answer the grub prompt part, I've used every variation of the boot command I can, and all that it tells me is that there is no kernel loaded.

I'm downloading the ISO file to burn a fresh LiveCD right now.

Thanks for all the answers, and I'll let you know if it doesn't work!

---

### Post by flooj on 2010-12-11
No dice.  I have the new Live CD and I don't click on install.  I just use the disk to boot it.
The way I understood you guys, it was that I just had to go and get my files and copy them to a flash drive?
There's no files there.  It's like a blank, fresh install.
So I'm still stuck.

---

### Post by owiknowi on 2010-12-11
ms wx ext2 driver and live CD don't work?

the hard way is using data recovery with for example the systemrescuecd ([http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)).

or search for other data recovery tools (ontrack, etc.)

hope this works.

and to be safe(r) in the future: never store your personal data on the same partition as the OS (als for ms wx).

---

### Post by azertyh on 2010-12-12
i used [testdisk](http://en.wikipedia.org/wiki/TestDisk) one month ago to recover data onto usb drive. it works great. and testdisk is in the repos.
read also the doc about [data recovery](https://help.ubuntu.com/community/DataRecovery).

---

### Post by johntaylor1887 on 2010-12-12
> **flooj said:**
> No dice.  I have the new Live CD and I don't click on install.  I just use the disk to boot it.
The way I understood you guys, it was that I just had to go and get my files and copy them to a flash drive?
There's no files there.  It's like a blank, fresh install.
So I'm still stuck.

You need to go to places>computer and click on the appropriate drive.

---

### Post by flooj on 2010-12-12
> **johntaylor1887 said:**
> You need to go to places>computer and click on the appropriate drive.

It wasn't there.  It was all empty.

---

### Post by flooj on 2010-12-12
> **azertyh said:**
> i used [testdisk](http://en.wikipedia.org/wiki/TestDisk) one month ago to recover data onto usb drive. it works great. and testdisk is in the repos.
read also the doc about [data recovery](https://help.ubuntu.com/community/DataRecovery).

Okay, I tried the testdisk, and after a few different scans through that program, I came upon these:
[IMG]http://tiny.cc/ti5xg[/IMG]

I looked deeper into all of those, and each one gave me this:
[IMG]http://tiny.cc/twb2h[/IMG]

So, unless there's a way to recover that, I guess I'm sunk.
Thanks for all the help, everyone!  I really appreciate it.  :D

---

### Post by owiknowi on 2010-12-14
> **flooj said:**
> Okay, I tried the testdisk, and after a few different scans through that program, I came upon these:
[IMG]http://tiny.cc/ti5xg[/IMG]

I looked deeper into all of those, and each one gave me this:
[IMG]http://tiny.cc/twb2h[/IMG]

So, unless there's a way to recover that, I guess I'm sunk.
Thanks for all the help, everyone!  I really appreciate it.  :D

the ext2 extension for ms wx to read/write linux partitions didn't work either?

have successful recovered data from a completely erased - not wiped - hdd with the systemrescuecd.

---

### Post by flooj on 2010-12-16
> **owiknowi said:**
> the ext2 extension for ms wx to read/write linux partitions didn't work either?

have successful recovered data from a completely erased - not wiped - hdd with the systemrescuecd.

I'm not sure I know what you mean.  I'm a very basic beginner, here.  :)

---

### Post by owiknowi on 2010-12-17
> **flooj said:**
> I'm not sure I know what you mean.  I'm a very basic beginner, here.  :)

i meant that if you want to recover data from an existing linux partition you can either use a data recovery program (as on the systemrescuecd) or, so i'm told, use [http://www.fs-driver.org/](http://www.fs-driver.org/) for windows.

the latter is an extension for ms windows which enables it to read linux partitions. by default windows only can see its own filesystems.

if i'm still not explaining it the right way don't hesitate to let me know!

btw: if one tells you to be an expert, don't believe it. ; )

---

### Post by flooj on 2010-12-17
> **owiknowi said:**
> i meant that if you want to recover data from an existing linux partition you can either use a data recovery program (as on the systemrescuecd) or, so i'm told, use [http://www.fs-driver.org/](http://www.fs-driver.org/) for windows.

the latter is an extension for ms windows which enables it to read linux partitions. by default windows only can see its own filesystems.

if i'm still not explaining it the right way don't hesitate to let me know!

btw: if one tells you to be an expert, don't believe it. ; )


I installed the IFS drive reader (the second thing from fs-driver.org) and it can't find the linux partitions.  
Am I just not understanding, or am I right in thinking that my partitions are just gone?

---

### Post by owiknowi on 2010-12-18
> **flooj said:**
> I installed the IFS drive reader (the second thing from fs-driver.org) and it can't find the linux partitions.  
Am I just not understanding, or am I right in thinking that my partitions are just gone?

if that driver doesn't work boot from a live cd like ubuntu, knoppix or partitioning cd's like
gparted ([http://downloads.sourceforge.net/gparted/gparted-live-0.4.0-1.iso](http://downloads.sourceforge.net/gparted/gparted-live-0.4.0-1.iso)) or
pmagic ([http://downloads.sourceforge.net/partedmagic/pmagic-5.6.iso.zip](http://downloads.sourceforge.net/partedmagic/pmagic-5.6.iso.zip)) cd

they show the existing partition table.

---

### Post by flooj on 2010-12-18
I didn't use one of those two that you suggested, and I can't remember the name of what I used.  Regardless, the partition table for the linux partitions was corrupted, so there's not much point in stressing out further.  
I think I'll just reinstall; the backup I had on my flash drive was a month more recent than I'd thought, so everything's pretty well intact.
Thanks for all the help, especially owiknowi.  :)  I really appreciate it, and if I have anything else to ask, I'll be back.  :D
Happy Holidays!

---

### Post by owiknowi on 2010-12-19
you're welcome!

if you consider a complete re-installation of ms windows and linux take a look at herman's very good instructions:
[http://members.iinet.net.au/~herman546/](http://members.iinet.net.au/~herman546/)

but please do feel free to ask anything, any time.

best regards, owiknowi

---

