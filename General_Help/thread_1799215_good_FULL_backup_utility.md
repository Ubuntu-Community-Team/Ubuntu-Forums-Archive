---
title: "good FULL backup utility"
date: 2011-07-07
forum: General Help
---

### Post by liquidmonkey on 2011-07-07
i'm using ubunut 10.10 and have installed all kinds of stuff and don't want to loose it all should something happen so i'd like to make a full system backup of EVERYTHING.

i should also mention i'm running 10.10 through virtual box but i don't think that matters too much...or?


anywho, the backup utilities i've seen so far only seem to be a glorified synchronization system and are not backing up the entire system like win7 does for example.

any suggestions would be greatly appreciated, thank you in advance :)

oh, and i would really prefer a GUI as i'm not so fond of the command line stuff :(

---

### Post by seawolf167 on 2011-07-07
If you are only running it in VBox, you can simply copy the disk image that was created as the virtual drive for your running system. A restore would just involve pointing a new VBox instance to that image.

If, however, you want to backup your Window system with everything on it (including the VBox install), then I suggest using [Clonezilla]("http://www.clonezilla.org"). You can image the entire hard drive (including boot sectors and the MBR) to an external hard drive. A restore would put your computer *exactly* as it was when you cloned it.

---

### Post by liquidmonkey on 2011-07-07
this is interesting cause i did a windows backup an hour ago and it only took the windows stuff. i was hoping it would take the VB ubuntu as well but no luck.

u mention i can just copy the VB image (which has ALL the ubuntu stuff) but where can i find that image?

i like your clonezilla idea but its not incremental and i have to reboot everytime which is kind of annoying but still might give it a try later on.

thanks!

---

### Post by collisionystm on 2011-07-07
> **liquidmonkey said:**
> this is interesting cause i did a windows backup an hour ago and it only took the windows stuff. i was hoping it would take the VB ubuntu as well but no luck.

u mention i can just copy the VB image (which has ALL the ubuntu stuff) but where can i find that image?

i like your clonezilla idea but its not incremental and i have to reboot everytime which is kind of annoying but still might give it a try later on.

thanks!

Its in your My Documents folder, Under Virtualbox. I am sure your Windows backup grabbed it. However, you should never leave your virtual ubuntu running durring any kind of backup or copy. You can corrupt the disk.

---

### Post by Jacobonbuntu on 2011-07-07
> **liquidmonkey said:**
> this is interesting cause i did a windows backup an hour ago and it only took the windows stuff. i was hoping it would take the VB ubuntu as well but no luck.

u mention i can just copy the VB image (which has ALL the ubuntu stuff) but where can i find that image?

i like your clonezilla idea but its not incremental and i have to reboot everytime which is kind of annoying but still might give it a try later on.

thanks!

The VB image is on your harddisk, depends on where you located that. If you never changed the directory it will be in /home/yourname/Virtualbox VMs

I guess a copy of that is indeed the perfect clone :P

---

### Post by seawolf167 on 2011-07-07
> **collisionystm said:**
> Its in your My Documents folder, Under Virtualbox. I am sure your Windows backup grabbed it. However, you should never leave your virtual ubuntu running durring any kind of backup or copy. You can corrupt the disk.

Maybe (double check to make sure!), and yes, good advice. 

I would check to ensure that it did indeed take it. If it didn't, check your backup settings for something to the effect of "do not backup files over XYZ in size". It may have been skipped if you had this on and your virtual disk was like 10 GB in size or something. It could also be skipping certain file types by default (like iso, vdi, vmdk, vhd, etc.)

---

### Post by liquidmonkey on 2011-07-07
yup, found the image, its a .vdi file of approx 10gigs.
not 100% sure if my windows backup grabbed it as i used the samsung utility and that seemed to split the backup image into 4.5gig sizes (for dvd i assume) so i can't really see what was taken.

either way, i can easily copy over the .vdi file now and sleep well knowing its a FULL back up in the ubuntu i use in VB.


thanks for all the help, much appreciated!!

---

### Post by seawolf167 on 2011-07-07
You should be good to go then - to restore it in the future, you'll need to open your new VBox instance, go to the Disk Manager and register your .vdi image, then open the settings menu of your virtual machine and add the .vdi as that machine's hard disk. Boot it up and everything should be the way you left it.

If this has been solved, please mark the thread as solved under thread tools

---

### Post by Frogs Hair on 2011-07-07
These are the two best options I know of for a full configuration backup , but they may require command line skills .

[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)

[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by chkl on 2011-07-07
Any ideas how to backup a Ubuntu 11 server (to another hard drive) on a regular basis ? 
I want to get a backup of the entire partition every night (or at least every week), preferably without manual interference...
Anybody who knows of a tried and tested software solution ?

Thanks in advance !

---

### Post by liquidmonkey on 2011-07-07
> **seawolf167 said:**
> You should be good to go then - to restore it in the future, you'll need to open your new VBox instance, go to the Disk Manager and register your .vdi image, then open the settings menu of your virtual machine and add the .vdi as that machine's hard disk. Boot it up and everything should be the way you left it.

If this has been solved, please mark the thread as solved under thread tools

yup, solved.

thanks for the help :)

---

### Post by liquidmonkey on 2011-07-07
> **Frogs Hair said:**
> These are the two best options I know of for a full configuration backup , but they may require command line skills .

[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)

[http://clonezilla.org/](http://clonezilla.org/)


thanks for the suggestions.
i think clonezilla would be the better if your ubuntu system size is greater than 4gigs.

---

### Post by seawolf167 on 2011-07-07
> **chkl said:**
> Any ideas how to backup a Ubuntu 11 server (to another hard drive) on a regular basis ? 
I want to get a backup of the entire partition every night (or at least every week), preferably without manual interference...
Anybody who knows of a tried and tested software solution ?

Thanks in advance !

Please start a separate thread with your issue and we'd be more than glad to help.

---

