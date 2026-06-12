---
title: "reading a backup file"
date: 2011-06-15
forum: General Help
---

### Post by sajansen on 2011-06-15
hey 

i had some problems with my hdd, i fixed most of the problems with "testdrive" or "testdisk" (cant remember :P)but i have some bad sections on my disk right whare my importent data is...i made a backup with "dd" from a live cd. i have the backup with a reading error or 5 so i guess most data is safe?? i have the backup of teh whole drive on an other hdd and now i need to get just a few folders out of it...i tried in windows but i can`t read it...poweriso can but not the privet folders like /var/ and that folder i need... an dyea i had a password on the account so i geuss that is part of the problem??

anyone a idea to read the backup file in windows...??

thanks

---

### Post by sanderd17 on 2011-06-15
The password can't be the problem, and Windows can't read ext4 partitions (or you need to install some modules, but that's very unstable). If you can't read it directly from a live CD, there is a big chance that the data you need is corrupted.

Check this to get some aditional tools for saving files: [http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

Once you have your files using a live CD, you can copy them to another HDD on a NTFS partition or on an USB stick.

---

### Post by sajansen on 2011-06-15
i can acces parts of teh files i need but its about 1 gig out of 21 gigs mostly pictures and some websites...when copying i get an IO error on the original source disk so i thout to make a backup of the entire disk with dd to get rid of the read errors... i havent tried reading the backup from teh live cd but i dont have the space on that computer to copy the files i need...so i was planning on reading them form winows couse that pc is way faster and has the space

but i cant run teh live cd on that pc coude of wireless driver problems and i need internet to install some programs before i can work with the data so its sort of hard to get it back from ubuntu

---

### Post by sanderd17 on 2011-06-15
Or replace the drive to the windows PC. You can run the live CD there to copy it over to Windows.

You can first do it without internet, or maybe with a wired network.

---

### Post by sajansen on 2011-06-15
Thanks... Ill give it a try

---

