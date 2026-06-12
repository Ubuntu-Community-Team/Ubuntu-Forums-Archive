---
title: "Fresh install to a new partition, how to get /home on old partition active/mounted?"
date: 2012-05-25
forum: General Help
---

### Post by Razmear on 2012-05-25
OK, it's been a lomg day of working on the wife's PC, so forgive any stupidity in my questions. 

This morning, her Kubuntu 12.4 pc would not boot, after several hours of fruitless troubleshooting the problem I decided to do a new install.

I have created a new 90gig partition on her drive and installed a fresh copy of Kubuntu 12.4 which I am working in now. 
Her old data and /home folder are still safe in a 350gig partition on the same drive. 
My goal is to get her old /home on the old partiton to become a seperate /home partition, and then to remove all the unneeded files from the old OS install.
Any pointers to novice level How-To's or suggestions on the best way to get this done would be appriciated. Time for a smoke break....

---

### Post by oldfred on 2012-05-25
I do not know how to houseclean an old install to make it just /home. It would entail removing all the system files and promoting /home/$USER to the top level or root of the partition.

If you want to move to a new partition. Also shows how to edit to make new partition your /home in fstab.

To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

When you have all your data in a separate /home you will find your / is pretty small. I just moved all data but not hidden settings, but also some hidden folders with data to a data partition. Then my /home without any data is less than 1GB and my full install is about 7GB with lots of apps installed. I use a 25GB / (root) partition.

---

### Post by Razmear on 2012-05-25
Thanks Fred, 
I was using the document you linked to, went thru all the relevant steps and got the error Cannot enter home directory. Using /. when I tried to log back in after rebooting. 
I used the Install disk to get back into the system and re-edit the fstab to remove the mount for /home and swap back old_home to home so I can get back into the system again. 
I'm guessing it was a permissons error on the /home/Kelley directory so I'm doing a chown to the 'new Kelley' and will be trying again shortly. 

All the other files have been deleted from the old partition but the /home directory. What did you mean by "promoting it" to the top level? That's where it currently sits, so I'm a bit confused. Should the folder /home be in the home partition or should the top levels be the $user folders? 

Thanks,
Eric

---

### Post by Razmear on 2012-05-25
YES YES YES!!!
Well, that was my problem, I had /home inside of the /home partition. A sudo mv kelley .. took care of the problem and life is good again!

Thanks Fred!

---

### Post by oldfred on 2012-05-26
Glad it worked. :)

If you have permission issues:

.dmrc errors- drs305
[http://ubuntuforums.org/showthread.php?p=6161267](http://ubuntuforums.org/showthread.php?p=6161267)
.ICEauthority errors
[http://ubuntuforums.org/showthread.php?t=1590835](http://ubuntuforums.org/showthread.php?t=1590835)
chmod 755 /home/username
sudo chown $USER:$USER /home/username/.ICEauthority
sudo chmod 644 /home/username/.ICEauthority
sudo chmod 644 $HOME/.ICEauthority
look at the permissions on ~/.Xauthority, too. It often gets changed when ~/.ICEauthority gets changed. The same fix applies.

---

