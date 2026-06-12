---
title: "moving a huge amout of files advice. please"
date: 2011-07-27
forum: General Help
---

### Post by surfmonkee on 2011-07-27
so i have about 2 TB of 700mb avi files as data on disc

want to spread it across two 2TB ext usb drives (sata 3.5 inside the housing)

obviously i have to rip them to the laptop and then move to the ext hdd

(omg laborious little task)

**question**

am i better doing the ripping in meerkat or in a windows machine?

files need to be accessible by W7, XP, and meerkat to vlc player.

what should i format the discs to?

what would you suggest is a maximum amount of data to shift at one time?

any other tips welcome

---

### Post by karlson on 2011-07-28
> **surfmonkee said:**
> 
obviously i have to rip them to the laptop and then move to the ext hdd

**question**

am i better doing the ripping in meerkat or in a windows machine?


I am assuming you are talking about ripping DVDs, which presents all sorts of legal dilemmas and problems, so I don't think anyone would answer this one for you and it may even have this thread killed.

> 
files need to be accessible by W7, XP, and meerkat to vlc player.

what should i format the discs to?


For this you would want to have a drive formatted NTFS and formatted by XP.

> 

what would you suggest is a maximum amount of data to shift at one time?

any other tips welcome

You have to think about this in the following way, your speed of transfer and reliability of it is dependent of the USB controller and port so you should consider how much you transfer at a clip from that point of view.  I'd not transfer more then 20GB at a time.

---

### Post by HermanAB on 2011-07-28
AVI files?  So these are already ripped?  If so, just copy them with rsync.  (rsync uses checksums so the copy is guaranteed to be good).

---

### Post by surfmonkee on 2011-07-28
> **surfmonkee said:**
> so i have about 2 TB of **700mb avi files** as data on disc



nothing illegal there mr!

---

### Post by surfmonkee on 2011-07-28
> **HermanAB said:**
> AVI files?  So these are already ripped?  If so, just copy them with rsync.  (rsync uses checksums so the copy is guaranteed to be good).

thanks, genius solution :)

---

### Post by keithpeter on 2011-07-28
Hello All

I love rsync and lftp. I use one for backups and the other for incrementally publishing a Web site over sftp.

[http://www.theregister.co.uk/2010/09/24/sysadmin_file_tools/](http://www.theregister.co.uk/2010/09/24/sysadmin_file_tools/)

Different problem, the comments are funny as well. 

Shall we mark this as SOLVED?

---

