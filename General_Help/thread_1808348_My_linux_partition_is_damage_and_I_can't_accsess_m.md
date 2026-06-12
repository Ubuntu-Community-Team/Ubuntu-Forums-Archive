---
title: "My linux partition is damage and I can't accsess my files"
date: 2011-07-20
forum: General Help
---

### Post by kirill578 on 2011-07-20
Hey, Yesterday I extended my ubuntu partition with a free space that I had on my NTFS partition. It did get any problem. However, today I couldn't boot into ubuntu ( It was loading for about half an hour ). then I reboot and I got some GRUB error, so I boot into live cd to repair the grub but then unfortunately I found out that my Linux partition is damaged.
I some how managed to repair it but the only folder that is there is "lost+found".  also there is written 62.8 GB free space, but this should be 112GB (unless there are some hidden files that i can access to )

So my question is: [COLOR=Red]Is there any way to access some file[/COLOR] ( to back them up)?

---

### Post by westie457 on 2011-07-20
> **kirill578 said:**
> Hey, Yesterday I extended my ubuntu partition with a free space that I had on my NTFS partition. It did get any problem. However, today I couldn't boot into ubuntu ( It was loading for about half an hour ). then I reboot and I got some GRUB error, so I boot into live cd to repair the grub but then unfortunately I found out that my Linux partition is damaged.
I some how managed to repair it but the only folder that is there is "lost+found".  also there is written 62.8 GB free space, but this should be 112GB (unless there are some hidden files that i can access to )

So my question is: [COLOR=Red]Is there any way to access some file[/COLOR] ( to back them up)?

What program did you use to do the partition adjustments?

If you used Gparted then you should not had any problems.

As for the recovery/back up of your files '[testdisk]("http://www.cgsecurity.org/wiki/TestDisk")' is recommended.

---

### Post by Quackers on 2011-07-20
Try opening gparted from the live cd desktop and right-click on the affected partition and select "check" and see if anything is reported.

---

### Post by kirill578 on 2011-07-20
> **westie457 said:**
> What program did you use to do the partition adjustments?

If you used Gparted then you should not had any problems.

As for the recovery/back up of your files '[testdisk]("http://www.cgsecurity.org/wiki/TestDisk")' is recommended.

I used Gparted. I've just downloaded testdisk...

---

### Post by kirill578 on 2011-07-20
I scanned the disk with DISKTEST, however I haven't managed to find my home folder
The only thing i found was the system root folder, but there is no /home

There is a a screenshot attached

EDIT: I tried to repair it with Gparted i got an error: "An error occurred while applying the operations"

---

### Post by alphaamanitin on 2011-07-20
When you have massive damage to a file system everything gets tossed into the Lost and Found if I remember correctly.  Quit messing with the damn thing before you make it worse.  Immediately back up the drive with something like the dd command.  When I accidentally deleted my windows xp HD (the entire drives partitions) in gparted and then reformatted it to FAT32 I used the dd command to clone the drive to a new HD.  This way one can work from the clone to recover the files confident that the original will still be available no matter what you do to the back up.  

Hopefully you didn't encrypt your home folder.  It can still be recovered I think, but the steps are a bit harder.

This website may help a bit but there are plenty of websites and threads on here that deal with recovery of files in the lost and found folder: [http://karuppuswamy.com/wordpress/2010/06/09/how-to-recover-files-from-lostfound-after-fsck-in-linux-how-i-did-it-in-ubuntu/](http://karuppuswamy.com/wordpress/2010/06/09/how-to-recover-files-from-lostfound-after-fsck-in-linux-how-i-did-it-in-ubuntu/)

AlphaA

---

### Post by kirill578 on 2011-07-20
THANKS!!! that worked I found my home folder!!! :P

---

### Post by alphaamanitin on 2011-07-20
> **kirill578 said:**
> THANKS!!! that worked I found my home folder!!! :P

Great, but don't go messing around too much until you are confident you know the steps to recover the data.  I would hate for you to lose the data after finding.  Though I believe it is very unlikely the data will be over-written because it isn't deleted or anything, just in a different folder.

AlphaA

---

