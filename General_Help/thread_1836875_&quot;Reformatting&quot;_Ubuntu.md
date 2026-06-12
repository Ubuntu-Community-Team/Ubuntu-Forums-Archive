---
title: "&quot;Reformatting&quot; Ubuntu"
date: 2011-08-31
forum: General Help
---

### Post by camelface on 2011-08-31
So this is what I would like to do before the semester starts:

Uninstall everything on my computer (Ubuntu 10.10, games, programs, etc) while keeping my data (movies, music, etc) and reinstalling Ubuntu 10.10 (the same version as before) to give my computer a fresh breath. 

How can a newb do this? To be honest, burning DVDs or getting an external hard drive is out of the question and too time consuming for me atm. 

Thank you!

---

### Post by thatguruguy on 2011-08-31
Is your home directory in a separate partition?

---

### Post by kyphi on 2011-08-31
> To be honest, burning DVDs or getting an external hard drive is out of the question and too time consuming for me atm.

You have got me there.

You could try to create a partition on your existing hard drive and transfer your data to that partition.  Just make sure that when you reinstall that you do not overwrite the new partition.  Seems risky to me - better get an external medium to save your data.

---

### Post by camelface on 2011-08-31
All my stuff is in one common area. I built the computer from parts and installed Ubuntu on a clean slate. There are no partitions and just one user. 

To start with, how do I reinstall Ubuntu? I did not observe any ready-made formatting, ubuntu removal or re-installing tools at all. Are there any? 

But anyway, there is no hurry as the current state of my computer than it would have been after 1 year of use with Windows, that's for sure. It is still fast but getting a bit weird sometimes (the software: the menus, the brower, etc).

---

### Post by coldraven on 2011-08-31
"It is still fast but getting a bit weird sometimes."
If it is your hard drive failing a re-install won't help.
Your priority is to save some pennies a buy an external hard drive. What you are doing is keeping all your eggs in one basket. Bad idea :(
You can always start copying and then go to bed :)
Why am I typing this at 04:30?

---

### Post by camelface on 2011-09-01
Ok, so I decided I will back up my essential data on DVDs and blow the computer up. 


1. How do I format? Do I need to press some key on start-up to enter the BIOS or what?

2. I feel like trying something new, and installing an older version (I will eventually go back to 10.10 if I am not satisfied). So are there any versions of Ubuntu you would like to suggest for their stability and smoothness, or is it useless as the newer versions have the essence of the old ones inclusively?

Thank you!

---

### Post by desnaike on 2011-09-01
The ubuntu livecd and most every linux livecd format during the install process so no need to do it before hand.
I would use gparted and create a small partition say 10-15 gigs if you can spare it and copy your data to it then during the install of the new os tell ubuntu to use sda/sda1 to install into, the small partition you created and formatted to say ext4 will be sdb/sdb1.

---

### Post by holycow131415 on 2011-09-01
Yep, you need to backup your data on a usb drive or an external hdd is a safer bet than dvds. Ubuntu formats your computer for you when you start to install the OS on the hdd from the CD.

---

### Post by camelface on 2011-09-01
> **holycow131415 said:**
> Yep, you need to backup your data on a usb drive or an external hdd is a safer bet than dvds. Ubuntu formats your computer for you when you start to install the OS on the hdd from the CD.


What is wrong with DVDs? I do not have enough memory on USB and do not own an external HD. I guess I can put the important stuff on USB. 

I just thankfully remembered to backup my evolution mail, contacts, etc. My hotmail account is completely downloaded by pop3 to my computer and definitely need to keep that. In evolution I went File>Backup Settings and saved the "evolution-backup.tar.gz" file. Is this is the file I need to reload everything? I just want to make sure.

---

### Post by holycow131415 on 2011-09-01
> **camelface said:**
> What is wrong with DVDs? I do not have enough memory on USB and do not own an external HD. I guess I can put the important stuff on USB. 

I just thankfully remembered to backup my evolution mail, contacts, etc. My hotmail account is completely downloaded by pop3 to my computer and definitely need to keep that. In evolution I went File>Backup Settings and saved the "evolution-backup.tar.gz" file. Is this is the file I need to reload everything? I just want to make sure.

DVDs could always get scratched, or not burn correctly, and depending on how much you need to back up it could take a lot of them.

---

