---
title: "Accessing floppy drive"
date: 2011-09-16
forum: General Help
---

### Post by TechMansoor on 2011-09-16
I'm really starting to lose faith in Linux. This is definitely anger talking, but its just ridiculous how windows 98 does a better job of understanding permissions and mounting floppy drives...

All I want to do is write to this floppy I inserted via my usb floppy drive.

The file, the drive says i'm the owner, yet I get a:

"Sorry, could not change the permissions of "disk": Error setting permissions: Read-only file system"

when trying to change permissions to read and write..

the crazy thing is though..I'm the owner!!!!!!!!

What do i need to do to resolve..any help would be awesome..

thanks

---

### Post by haqking on 2011-09-16
> **TechMansoor said:**
> I'm really starting to lose faith in Linux. This is definitely anger talking, but its just ridiculous how windows 98 does a better job of understanding permissions and mounting floppy drives...

All I want to do is write to this floppy I inserted via my usb floppy drive.

The file, the drive says i'm the owner, yet I get a:

"Sorry, could not change the permissions of "disk": Error setting permissions: Read-only file system"

when trying to change permissions to read and write..

the crazy thing is though..I'm the owner!!!!!!!!

What do i need to do to resolve..any help would be awesome..

thanks


First of all Windows 98 has no permission structure to speak of.

Second of all obvious but all the same, does the floppy have the tab over preventing from writing to it ?

---

### Post by TechMansoor on 2011-09-16
Windows 98 has permissions(not in traditional sense, but I count the file attributes in being all inclusive), owners, and you can properly utilize floppy drives in it!!!

That goes with out saying with the floppy actually being writable via its locking notch...


I'm just saying..

Ubuntu suppose to the baddest(good) OS literally, most customizable, most secure, yet it has consistent troubles with minute tasks such as mounting floppy drives????

In any case, I've tried every chmod combination there is, and still, a damn floppy comes up as unreadable when in actuality, ubuntu specifies that I am the owner...If I'm another user, then thats fine but this is ridiculous!!!!!!

---

### Post by haqking on 2011-09-16
> **TechMansoor said:**
> Windows 98 has permissions(not in traditional sense, but I count the file attributes in being all inclusive), owners, and you can properly utilize floppy drives in it!!!

That goes with out saying with the floppy actually being writable via its locking notch...


I'm just saying..

Ubuntu suppose to the baddest(good) OS literally, most customizable, most secure, yet it has consistent troubles with minute tasks such as mounting floppy drives????

In any case, I've tried every chmod combination there is, and still, a damn floppy comes up as unreadable when in actuality, ubuntu specifies that I am the owner...If I'm another user, then thats fine but this is ridiculous!!!!!!


You probably need to change the fstab to mount as rw instead of ro.

[http://chris-linux.blogspot.com/2007/02/mounting-devices.html](http://chris-linux.blogspot.com/2007/02/mounting-devices.html)

[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

as for baddest(good).  Linux is what you make it, it is differnt to what you are used to yes and many of us find it very useable and enjoyable.

as for locking notch, nothing goes without saying in computer support.

and as for file permission and using floppys, no comment.

remember also it is not a regualr floppy but a USB device.

Hope the links help, change the mount to rw instead of ro in the fstab i suspect will solve it.

---

### Post by TechMansoor on 2011-09-16
ill give it a shot

---

### Post by Synoc on 2011-09-16
Linux security is a two-edged sword. because it is so secure it requires you to sometimes jump through some hoops. These can be gotten around in some case, not in all. Do not loose faith in Linux. Learn it, embrace it, remember every problem you have makes you that much better a user when you get passed it.

---

### Post by Habitual on 2011-09-16
> **haqking said:**
> First of all Windows 98 has no permission structure to speak of.

Amen.

---

### Post by spcwingo on 2011-09-16
> **Synoc said:**
> Linux security is a two-edged sword. because it is so secure it requires you to sometimes jump through some hoops. These can be gotten around in some case, not in all. Do not loose faith in Linux. Learn it, embrace it, remember every problem you have makes you that much better a user when you get passed it.

This ^

---

### Post by dkolars on 2011-09-22
Well, i'll chime in here... after about 2 1/2 yrs. of Linux, I still find it extremely frustrating... just got a USB floppy drive (MPF82E-U5), and was able to mount it by adding a dir ("floppy") to the "media" subdir, then running in terminal:  "sudo mount /dev/sdm /media/floppy -t vfat".  Mounted just fine, copied a file off a floppy using Nautilus (Krusader will not see the floppy drive), and then added "/dev/sdm             /floppy         auto    rw,noauto,sync 0" to my fstab file...

So, re-booted, and attempted to copy the file to a blank floppy by simply drag/drop in the Nautulis window.  Fine, just fine.

Nope, it just put it in the /media/floppy sub-dir on my HDD, and did NOTHING with the floppy drive.

Floppy drive says it is owned by root, is read-only, and even when I go in as root, I cannot change the permissions to allow anyone to write to the drive.

Gparted does not see the floppy drive, so there is no changing any permissions available to me that I know of.

I, like Techmansoor, really do not like the root/user structure that Linux has.  I'm the only user on my computer, and the process needed to simply copy or edit a file is sometimes ridiculous.

So, that said, what needs to be done to have the floppy drive recognized as a USB stick is recognized:  as in, instantly?  And how can I change the permissions to allow access by everyone, meaning ME, THE ONLY USER?  

I'm a retired Win NT Admin, and at times like this, I really miss NT :-(

---

### Post by zitch on 2011-09-23
> **dkolars said:**
> ...

I'm a retired Win NT Admin, and at times like this, I really miss NT :-(

As a former Windows NT admin, I've yet to ever miss it after a decade working with Linux... ;)  There are things to like about the later Windows Server releases though...

Not much I could do to help here, but I do have a suggestion of being patient.  I doubt many people today have ever had to work with a floppy drive in linux; I know that the last time I used floppy disks in Linux was installing various Linux distributions on an old 486 I had in 1999 or so (and I ended up installing Slackware from floppies then; that system ended up being my main file and mail server for some time with a 40 GB drive in it...). My next Linux laptop would likely not even have a DVD drive in it, as the drive in my current laptop only serves to annoy me when I accidentally hit the eject button once in a while. I know how to install Ubuntu using only USB flash drives now, and I actually prefer doing it that way too.

Basically, I wouldn't be surprised if supporting floppy drives have fallen off out the wayside in most modern Linux distros; Not that linux doesn't support them, but the knowledge on how to use them is largely forgotten.  Yes, I can see this being frustrating, but I can only suggest doing research on Google and trying to figure this out.  

I'd help you out, but I only have one floppy drive in this house; it's on the Pentium III system that was my gaming system when I was messing around with linux on the above-mentioned 486 system and it's now running as my internet router (running the FreeBSD-based pfSense), and even if I was willing to take that apart (and take the wrath of the fiancee for taking the Internet down ON PURPOSE... ;) ), I don't think I even have a floppy disk around here to even test with...

---

### Post by dcstar on 2011-09-23
> **dkolars said:**
> Well, i'll chime in here... after about 2 1/2 yrs. of Linux, I still find it extremely frustrating... just got a USB floppy drive (MPF82E-U5), and was able to mount it by adding a dir ("floppy") to the "media" subdir, then running in terminal:  "sudo mount /dev/sdm **/media/floppy** -t vfat".  Mounted just fine, copied a file off a floppy using Nautilus (Krusader will not see the floppy drive), and then added "/dev/sdm             **/floppy**         auto    rw,noauto,sync 0" to my fstab file...

So, re-booted, and attempted to copy the file to a blank floppy by simply drag/drop in the Nautulis window.  Fine, just fine.

Nope, it just put it in the **/media/floppy** sub-dir on my HDD, and did NOTHING with the floppy drive.
..........

I suppose if these are **not** all the same then you will have issues.

---

### Post by mörgæs on 2011-09-23
Thread title changed to a more descriptive one.

---

