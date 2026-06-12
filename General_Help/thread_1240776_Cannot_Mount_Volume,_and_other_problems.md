---
title: "Cannot Mount Volume, and other problems"
date: 2009-08-15
forum: General Help
---

### Post by stolenfat on 2009-08-15
Let me open with saying your guys have helped me so much in the past that i thought you'd be the fellows to run my new problems by.  This isn't entirely a linux/ubuntu, theres a splash of windows in it too.

I was running windows, the only partition on my drive, and got a blue screen of death.  Upon restarting 'NO OPERATING SYSTEM FOUND' was displayed.

I instantly thought the smartest thing to do was to pop in my ubuntu live CD and back up my data (it had been about 2 months since my last back up).  

One key thing to note here is Ubuntu recognizes my 250 GB drive, but tells me it cannot be mounted. 

I get two read outs:

$LogFile indicares unclean shutdown (0, 0) Failed to mount '/dev/sda1':
Operation not supported Mount is denied because NTFS is marked to be in use.

and then (possibly due to a communication error between ubuntu and the drive)

DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.


After some research, i found some possible fixes. A few include the windows recovery disc with fixboot (which returns 'Fixboot cannot open partition'), fixmbr, which does nothing, and chkdsk /r and chkdsk /p which returns "specified drive not valid"

Saddened, I decided to load the BIOS and discovered that the bios does not detect a hard drive.

Which brings me full circle... how can ubuntu detect (see) my 250 gig drive, while my BIOS reads NO HARD DRIVE?

If Ubuntu can 'see' it, is there a chance to fix it.  Any other ideas that might work?

Also, a clean install of ubuntu just lagged on and on and got no where, Gparted never loaded up when opened.  A fresh install of windows told me that the set up did not find any hard drives. 

Also my drive makes no CLICK CLICK CLICK sounds like there is physical damage.

Any help? Ideas?  Thank you geniuses!

---

### Post by sigixv on 2009-08-15
Sounds to me that your disk is broken.
Bios might not show the disk as it produces errors but info is transmitted that there's something present... (i had a similar experience with my broken RAM)

---

### Post by Screwdriver0815 on 2009-08-15
seems like the harddisk is broken.

But you can try to save some data:

let it cool down, put it into a case for external harddrives, plug it via USB at  another computer and try to get into it/ copy some data

maybe after some time letting it cooling down it works like nothing has happened (so did one over here) but be aware that it can crash again at any time.

---

### Post by mwjones on 2009-08-15
The BIOS may be buggy causing it to not see the hdd.  I had an ABit board that would only see drives under certain configurations (one SATA hdd and one PATA CD-RW at certain positions, for example).  

The other suggestions on this thread are good, I just wanted to add in another.

You could attach another drive to the system, either internally or externally, and dd your first drive over to an image.  You will need 250GB of free space on the second drive.  Here is the code asserting your broken hdd is /dev/sda and the second hdd is /dev/sdb with a partition on /dev/sdb1 with more than 250GB of free space and a filesystem that can handle a 250GB file and it is mounted at /mnt/sdb1:

```
sudo dd if=/dev/sda of=/mnt/sdb1/windows.dd
```

That will try to get every byte off of the broken hdd and place it in an image in the root of /mnt/sdb1.  

Like I said, this is just another option you could pursue.  The other suggestions are also good.

---

### Post by stolenfat on 2009-08-16
well guys thanks for the suggestions, nothing really helped.

I cant put it into a usb holder/connected because i dont have one, and its an internal lap top hard drive. 

but my last back up was two months so im not completely screwed with my data.

I think i will concur that my hard drive is just broken and unfixable.

Damn those blue screens of death.

---

