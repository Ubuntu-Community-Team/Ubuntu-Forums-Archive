---
title: "how to make Filezilla save to my external hdd"
date: 2010-01-31
forum: General Help
---

### Post by kjell75 on 2010-01-31
Hi!

I'm quite new to Linux/ Ubuntu, got it yesterday actually. I have no experience with the Linux system from before.

Installed Filezilla FTP-client, and wants to save the downloaded files to my external OneTouch4 HDD.

In Windows, you've got letters for different drives, like c: d: and so on.

I understand my external HDD is /dev/sdb1/ in Ubuntu (9.1).

My local place is just called "/" in Filezilla, I guess this refers to my root. It shows different folders, like bin, boot, cdrom, dev etc. 
When I try to type in /dev/sdb1/ here, I just get an error saying it does'n exist, or cannot be accessed. 

I don't understand this system yet.

I hope some of you understood this, and can help me with an answer.

PS: My external hdd is mounted, it has its own icon on the desktop. 

Regards, kjell75

---

### Post by kjell75 on 2010-02-03
Bump

I find sdb1 in folder /dev, but when I try to access/ open it, I get the message 

Filen '/dev/sdb1' kunne ikke åpnes:/nIngen program har blitt assosiert med denne filtypen i systemet ditt.

which translated from Norwegian to English is: "the file dev/sdb1 could not be opened/ no program has been assosiated with this type of file in your system".

Anyone know how to sort this out, please?

Prettty please?

---

### Post by indytim on 2010-02-03
I usually do my partition mount points in /media ie. /media/sda7.  Once it's mounted it's pretty easy to navigate to the destination location within Filezilla for getting or putting.

IndyTim

---

### Post by kjell75 on 2010-02-03
Thanks!! :popcorn:

That solved it!

Linux seems OK, but I really can't make any sense of the machine structure yet, always used win pc's.

---

### Post by KillerKellerjr on 2010-02-03
> **kjell75 said:**
> Thanks!! :popcorn:

That solved it!

Linux seems OK, but I really can't make any sense of the machine structure yet, always used win pc's.

Here are some great articles how the Linux structure works:

[Link]("http://www.nixtutor.com/linux/understanding-the-linux-directory-layout/")
or
[Link]("http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilestruct.html")

They sure helped me out a when I made the switch about a year ago.

---

