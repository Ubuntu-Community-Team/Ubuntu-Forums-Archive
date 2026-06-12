---
title: "Backing up the entire system..."
date: 2010-09-05
forum: General Help
---

### Post by speedracer2010 on 2010-09-05
I have read a great many articles (using the advanced search feature here) about backing the system up. I am in the Win world currently hoping to cross over to the Ubuntu world. While in the Win world I have had to restore my system on many an occasion. Either due to hard drive failure, system malfunction or just 'because' failures. In any event I have used programs such as Acronis, NTI and other programs to accomplish this task. They backup ALL data on the drive to a separate hard drive and then allow me to restore ALL back onto the new or reformatted hard drive = right where I was before the program began. It seems that 'Remastersys" can ONLY back up to a DVD so it is limited to 4+gig. Several other 'commercial' suggestions worked on RAID or SERVER systems mine is NOT. One gentleman went to great lengths in providing a script but in the end (as I understand it) still required Ubuntu to be installed and then restoring the data onto the newly installed operating system. Don't want to do the process twice. So, and I believe a great many are still asking and looking for this solution, is there a program that will make a TOTAL copy of the hard drive and save it to a device of choice (in my case an external hard drive) and then WHEN disaster strikes use a boot disc of sort and then RESTORE from that device back onto the hard drive of choice?? I have installed Ubuntu 3 times from scratch in the last 2 weeks after getting various portions installed and somewhat running. NOW that I am getting further along I don't want to start all over again WHEN I do something stupid (and I will). SORRY for the long post but really want to keep what I have and go forward not backwards.... THANKS to all..

---

### Post by howefield on 2010-09-05
> **speedracer2010 said:**
> In any event I have used programs such as Acronis, NTI and other programs to accomplish this task. They backup ALL data on the drive to a separate hard drive and then allow me to restore ALL back onto the new or reformatted hard drive = right where I was before the program began.

Have a look at Clonezila, in some ways similar to Acronis, but not as point and clicky ;-)

Don't let that stop you, it is very much easier to follow than it appears.

clonezilla.org

---

### Post by TimEnid on 2010-09-05
i downloaded the zip file, but am not sure how to get it installed. i was able to burn the live cd to a disk for when i need to restore, but how do i run the actual clonezilla program, and choose where to save my backups?
> **howefield said:**
> Have a look at Clonezila, in some ways similar to Acronis, but not as point and clicky ;-)

Don't let that stop you, it is very much easier to follow than it appears.

clonezilla.org

---

### Post by perspectoff on 2010-09-05
See:

[http://ubuntuguide.org/wiki/Ubuntu:Lucid#System_Backup_and_Recovery](http://ubuntuguide.org/wiki/Ubuntu:Lucid#System_Backup_and_Recovery) and [http://ubuntuguide.org/wiki/Ubuntu:Lucid#System_Rescue_and_Cloning_Utilities](http://ubuntuguide.org/wiki/Ubuntu:Lucid#System_Rescue_and_Cloning_Utilities)

or

[http://kubuntuguide.org/Lucid#System_Backup_and_Recovery](http://kubuntuguide.org/Lucid#System_Backup_and_Recovery) and [http://kubuntuguide.org/Lucid#System_Rescue_and_Cloning_Utilities](http://kubuntuguide.org/Lucid#System_Rescue_and_Cloning_Utilities)

Clonezilla is a very good tool. It is best used as a LiveCD.

There are others, depending on your exact requirements.

---

### Post by howefield on 2010-09-06
> **TimEnid said:**
> i downloaded the zip file, but am not sure how to get it installed. i was able to burn the live cd to a disk for when i need to restore, but how do i run the actual clonezilla program, and choose where to save my backups?

I'm not sure what's in the zip file, I usually download the .iso file. (I guess the zip file just contains the iso). Burn as an image to a CD.

Then boot from it, you'll most likely do fine simply by following the defaults and selecting beginner mode. Once you have your image in the bag, you can mess around learning a little more.

Just read each "page" carefully, you'll first tell Clonezilla where you want the image putting, I'd leave it on the root of whatever disk/partition you want, and secondly tell Clonezilla what you want backing up.

---

