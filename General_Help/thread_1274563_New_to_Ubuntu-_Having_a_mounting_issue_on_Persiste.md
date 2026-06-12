---
title: "New to Ubuntu- Having a mounting issue on Persistent install."
date: 2009-09-24
forum: General Help
---

### Post by SonniDaze on 2009-09-24
I'm fairly new to Ubuntu and very impressed.  Its a very nice system from what I have seen.  I'm installed on to a USB thumb drive using a persistent install with 9.04.  Last night I bumped my USB stick while running the system and it froze up on me.  I had to power the machine down and restart.  After this happened I am unable to mount my windows drive that is installed into the computer.  I really need to be able to mount this drive to access files.  Does anyone have any ideas on how I would be able to fix this issue or any console command that will give me and error code or problem?

Thanks in advance for the advice I am going to receive.

Sonni.

---

### Post by The Cog on 2009-09-24
Have you booted Windows since? Doing so may perform a chkdsk that cleans up the problem.

That idea aside, we do need an error message. First you need to know what device your windows drive is - something like **/dev/sda1**. If you're not sure, the command **sudo blkid** will show you the partitions and their type - you're looking for an ntfs partition. Once you know the windows device number, try this command (using your windows drive's device number of course):
**sudo mount /dev/sda1 /mnt**
and post the result here. Remember it also helps to post the actual command you entered so that we can see if it somehow got mis-typed or not.

---

### Post by SonniDaze on 2009-09-24
If you can give me a pointer on how to do a screen capture I can send a little more info on the issue.  Doing the sudo mount command it did allow me to mount the drive.  It still is not allowing me to mount the drive by clicking places in the top menu bar and the drive itself.  The windows drive is sda1 and my usb drive is sdb1.  I have booted to the windows drive since this happened with out an issue.

---

### Post by SonniDaze on 2009-09-24
[ATTACH]129660[/ATTACH]

Found screen shot app.

Hope this helps.

Sonni.

---

### Post by SonniDaze on 2009-09-24
Bump.

---

### Post by SonniDaze on 2009-09-24
Solved the issue.

/dev/sda1 /media/disk fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0

was found in the mtab document, when I went to bash and cd /dev/sda1 and no mount was detected.  I reopened that drive under places and it mounted.

Thanks Cod for your help.

---

### Post by The Cog on 2009-09-25
> **SonniDaze said:**
> Solved the issue.

/dev/sda1 /media/disk fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0

was found in the mtab document, when I went to bash and cd /dev/sda1 and no mount was detected.  I reopened that drive under places and it mounted.

Thanks Cod for your help.

/dev/sda1 is the device interface to that partition - you can read and write the raw partition bytes from there. Something you probably don't want to do very often. /media/disk is called the mount point, which is always a directory, and is where the contents of the filesystem on sda1 appear when it is succesfully mounted. It is this mount point that you want to look in to read/write files on the partition. Trying to cd to /dev/something is a beginners mistake - one that I haven't made for, ooh, at least 10 hours now.

And it's the Cog, not Cod. A small wheel in a large machine, and an acronym for Cantankerous Old Git, both of which seem quite fitting for me.

---

