---
title: "How should I partition my drive?"
date: 2009-09-12
forum: General Help
---

### Post by bridgetothesun on 2009-09-12
So I have a 160gb harddrive on my laptop. Of the 160, for some reason only 150 is available for partitioning on Gparted.

So, this is what I want my system to be like. I want to have a partition for windows (whicher version), a partition for important files (documents, etc), and a partition for Linux. 

Here are the sizes I'm thinking:
Windows Partition: 50gb
Important Files: 75gb
Linux partition: 25gb

Should I make three primary partitions then? And should I resize my current windows partition (which takes up 125gb), to 75gb? 

Also what file system should I use? I know for the Windows partition I will leave it as NTFS. But for the other two, I have no idea. NTFS for the Important files partition as well? And then ext for the Linux?

The reason I want the Windows partition separate is because I will be doing a clean install of Windows 7 Pro when I get it so if the files on the partition are seperate from my important documents, it will be easier. 

Any help is appreciated.

Thanks.

---

### Post by Woody1987 on 2009-09-12
For Linux use ext4. For the documents, assuming you want to be able to access it from windows then NTFS as windows cant read ext without third-party software. You may also want to split your Linux partition into two partitions. One for root and the rest for home, i recommend about 5gb for root and 20gb for home if all your planning on giving it is 25gb.

---

### Post by Vaphell on 2009-09-12
shared partition - ntfs, both w7 and ubuntu will be able to use it without much hassle.
linux - of course ext
i would suggest creating additional partition for /home (which stores all your config files). That way in case of reinstall apps are configured just like they were before.

---

### Post by Essary on 2009-09-12
Read through this:

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

Sounds like you have it figured out already. I used NTFS for storage. Don't forget about your swap partition.

---

### Post by Woody1987 on 2009-09-12
> Sounds like you have it figured out already. I used NTFS for storage. Don't forget about your swap partition.

If he has at least 2gig of RAM he wont need a swap, i havent used swap in 3 years and when i did, it was almost never used.

---

### Post by Essary on 2009-09-12
> **Woody1987 said:**
> If he has at least 2gig of RAM he wont need a swap, i havent used swap in 3 years and when i did, it was almost never used.

Was not aware of that. Nothing I read mentioned it. Thank you.

---

### Post by bridgetothesun on 2009-09-12
Thanks for the help. 

Few questions:

So should I make all the partitions "primary"?

Also, will I be delegating which go to /root and which to /home during the Ubuntu installation?

Thanks.

---

### Post by Bartender on 2009-09-12
This is just my personal preference so take it as you will.  The only partition that NEEDS to be primary is the Windows boot partition.  Windows can't boot from within an extended partition.

Let's say you wanted to stick with primary partitions.  There's really no reason, but let's just say.  You make a Windows primary, an Ubuntu / primary, an Ubuntu /home primary, and a data primary.  You're done.  That's all she wrote.  What if you decided you wanted a swap after all?  You couldn't add it even if you intended to make it a logical partition because you're up against the stops.   

So I'd suggest one primary partition for Windows, then create an extended partition out of all the rest of the space.  Then you can create several logical partitions for Ubuntu and your data partition.

EDIT:  As to your other question, you create the partition first by picking a size and creating it.  Then "edit" the partition you want to use as /, and in the "Mount as" window select /.  The "Edit Partition" button is down at the bottom of the page.  Same thing for the partition you want as /home - edit it, mount as /home, you're done.  You'll also have to set the file type.  I've been choosing ext4 for everything but some folks are erring on the safe side and choosing ext3, at least for the /home partition.  I don't think I explained that very well - you basically pick a space that you want, then create the partition, then tell Ubuntu to mount it as / or /home or whatever.  You can create the data partition from within GParted too - just pick the size, create the partition, format it as NTFS.

---

### Post by bridgetothesun on 2009-09-12
Thanks for that reply. Very helpful for a newbie like me.

Now if you don't mind, can you please explain to me why I would want a /root partition and a /home partition and what the "root" and "home" signify?

---

### Post by Vaphell on 2009-09-12
root is the top level directory keeping all other dirs inside (that's why its mandatory), /home is one of them and it's the only one with the user specific things. The rest is pretty much an internal system stuff - libraries, system apps, etc.
/home dir is where user accounts are kept - each user gets his personal directory here, where all his customizations, preferences, files, etc are stored.

that way you have user stuff independent from system partition - you can reinstall system and users accounts are fine (you just say 'this is home partition right there, and don't format it'). After reinstall all configs work and your account works just like before. In case of a common single partition you'd have to backup files and configs to restore them later.

in fact you can create a partition for any of the system directories present at the top level of the linux file system ( /usr, /opt, /boot ... ) but from the user perspective benefits are much greater in case of /home.

---

### Post by bridgetothesun on 2009-09-12
thank you! I'll now partition with confidence.

---

