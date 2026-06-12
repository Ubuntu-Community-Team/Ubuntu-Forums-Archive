---
title: "Trouble Installing 6.06"
date: 2006-06-13
forum: General Help
---

### Post by wind0s on 2006-06-13
I'm trying to install Ubuntu 6.06 on my new laptop onto an external HD through an external CD reader. Whenever I go to install ubuntu, it tells me it is unable to install the swap files. Additionally, it stops at 15% each time. Any help would be appreciated.

---

### Post by paulmilliken on 2006-06-13
Are you trying to install to a usb hard disk drive?  I don't think it is possible to do this unless you can set your computer to boot from a USB device.

Paul

---

### Post by wind0s on 2006-06-13
My computer is set to boot from the USB. It gets to the install screen, but it stops at 15%

---

### Post by paulmilliken on 2006-06-13
I assume you can run Dapper as a "live" cd though?  I don't know the answer but I wonder if the usb-disk can't keep up with the speed required to write to disk when installing?  I have had speed issues when using usb-hard-disk-drives before.

Paul

---

### Post by Fittersman on 2006-06-13
ok, well i asked my teacher who recommended this and he said to use winrar to unpack the iso, then burn it on a cd. so i did that then when i tried to run it again it still says that when i change the primary loader thinger to cd-rom it tells me that it fails, so i dont know what to do.

and no, it wont run it live cd.

i do have alot of experience with this program though because i had to edit a bunch of files so that i oculd actually use it (this was a while ago though) so i really just need a refresher course here.

---

### Post by wind0s on 2006-06-13
That is irrelevant to the topic of this thread. I can get the download to start. It just freezes at 15%

---

### Post by aysiu on 2006-06-13
It sounds like a corrupted ISO.

Both Fittersman and wind0s should read this:
[http://www.psychocats.net/ubuntu/iso.html](http://www.psychocats.net/ubuntu/iso.html)

---

### Post by Fittersman on 2006-06-13
lol dam i guess this is the wrong place.... thought i was in my topic

---

### Post by aysiu on 2006-06-13
You may be in the "wrong" place, but you should still read the link I posted.

Hint: you're not supposed to unrar the .ISO file.

---

### Post by wind0s on 2006-06-13
I burnt the image using Nero. I'm pretty sure it burnt correctly as it loaded after the restart.

---

### Post by aysiu on 2006-06-13
You should read the link. It isn't just about burning it correctly.

There are two separate issues here:

Fittersman wasn't burning the ISO correctly. You, wind0s, however, probably have a corrupt ISO.

The link I posted above addresses both of those problems.

---

### Post by wind0s on 2006-06-14
I just verified the file, and it is not corrupted.

The exact error message I'm getting during installation is: "Failed to create a swap space."

---

### Post by aysiu on 2006-06-14
Did you, by chance, burn it at a high speed?

Installation failures generally stem from one of the following:
1. ISO corrupted during download
2. ISO corrupted during burn
3. Hardware failure

---

### Post by wind0s on 2006-06-15
I downloaded ubuntu from another mirror and burned it using a different program at a slower speed and it got me past that step. :) Now, after I prepare my mount points in step 5 of 6, it does the progress bar check or whatever and then does nothing else.

---

### Post by wind0s on 2006-06-15
I've designated only the root and swap space.

---

### Post by wind0s on 2006-06-16
Help?

---

### Post by aysiu on 2006-06-16
I have no idea.

If you've done a checksum and burned at a slow speed... I don't know what else could be wrong besides your hardware, but I doubt that's it.

---

### Post by metajet on 2006-08-06
Hi Wind0s,

I am having the same trouble, but have seen you were able to get past it. Can you tell me how you did it?

The machine I am trying to install to was an old win2000, given to me, but I did not have the admin password. So was hoping the installation would wipe the old info and I could have a Ubuntu only computer.

Thanks

---

### Post by metajet on 2006-08-14
Update

Have finally got it to work - did not seem to be Ubuntu - rather IBM's Deskstar (Deathstar) HDD, swapped it out last night and everything has worked fine since.

---

