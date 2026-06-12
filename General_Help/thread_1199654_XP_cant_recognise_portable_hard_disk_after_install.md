---
title: "XP cant recognise portable hard disk after install Ubuntu"
date: 2009-06-29
forum: General Help
---

### Post by ruru85 on 2009-06-29
Hi,

I am currently faced with a problem which i have no idea where to start. I selected to install Ubuntu entirely on my WD 500 GB portable hard disk. Thereafter, XP could not detect or recognise this hard disk anymore. There is no way i can access this hard disk in XP anymore.

However, Ubuntu could still recognise it this hard disk as the file system which I installed it on.

Would very much appreciate if someone could guide me through this mess. I would like to be able to detect this hard disk again in XP.

---

### Post by kokkus on 2009-06-29
Windows can't recognize it because you now have a Linux partition on your portable hard driver.

---

### Post by anaconda on 2009-06-29
> **kokkus said:**
> Windows can't recognize it because you now have a Linux partition on your portable hard driver.

That is true, but IF you installed ubuntu on the default filesystem (ext3) then you can access it from windows. by installing fs driver to windows.
[http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)


.

---

### Post by The Cog on 2009-06-29
Windows XP can't normally read Linux type partitions. Not Invented Here.

There are ext2/3 drivers available for windows though.
[http://www.google.co.uk/search?hl=en&q=windows+ext3+driver](http://www.google.co.uk/search?hl=en&q=windows+ext3+driver)

---

### Post by kokkus on 2009-06-29
But isn't that just SO recommended? I mean in windows you have fully admin access even as a user. One of the reasons why ubuntu is safe for hackers etc. is because you can't manage the system files in normal user mode.
With fs-driver you break parts of that security.

---

### Post by ruru85 on 2009-06-29
> **anaconda said:**
> That is true, but IF you installed ubuntu on the default filesystem (ext3) then you can access it from windows. by installing fs driver to windows.
[http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)


.
Thanks. This is helpful. I have installed the driver from the site above. The hard disk partitioned drives can now be read.

However, there is still an issue here. XP is still unable to read the contents of the drive, prompting me whether to reformat instead. Is there a better ext3 driver out there?

The driver provided above was originally for ext2.

---

