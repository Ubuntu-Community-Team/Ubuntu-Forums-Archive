---
title: "No 'along-side' option when trying to install 11.04"
date: 2011-08-20
forum: General Help
---

### Post by airspoon on 2011-08-20
Hello, 
 I'm trying to install 11.04 on an older HP nc6220 laptop that is currently running XP Pro. 

While running Ubuntu from the thumb-drive has been successful, with everything working so far, the installation doesn't seem to be giving me all of the options that previous installs on other machines have.

For instance, when I click on the option to install Ubuntu, I'm only getting the option to install 'over' XP Pro and not along side it.  There is however one other option, 'something else', where I believe that you can manually create the partitions, however it's all greek to me. 

Is there a specific reason why I'm not getting the option to install 'along-side' XP pro? 

For whatever it's worth, when it does the checks just after clicking the 'install' option, it says that I'm good to go -as far as available space and internet connection. 

Do I just have to manually create the partitions, or is there anyway to get the option to install 'along-side' XP pro? If it's the former, how do I go about doing that?

Thanks!

---

### Post by Rasa1111 on 2011-08-20
Every time Ive installed 11.04 on the numerous machines i have..
I am pretty sure Im always given the option to 'install alongside'. 
Not sure what's up on your end, bud. 

But Im happy to see you've stuck with Ubuntu! :) <3
Good luck, man.

---

### Post by Quackers on 2011-08-20
It is possible that your current Windows system is using all 4 of the available primary partitions. Check that in Windows Disk Management screen. If that is the case you will need to delete one partition (probably HP TOOLS) and then probably shrink another partition (C: ) to create more free space for Ubuntu to install into. 
The shrinkage can be done from within the Windows Disk Management screen, but the C: partition should be defragmented first.
Once these steps have been taken the Ubuntu installer should then offer the "install alongside" option.

---

### Post by airspoon on 2011-08-20
Thanks Raza.

Quakers, there is only a single partition on the drive. That's it.

---

### Post by Quackers on 2011-08-20
Does that single partition use up all of the disc space? If so reduce its size so that some free space is left, then try Ubuntu again.

---

### Post by airspoon on 2011-08-20
it's a 75.2 gb drive, with 30 gb of free space. However, all of that is within the single partition. Is there a way to reduce the size of that partition without creating another partition?

Edit to add: Could it possibly be that I just need to defrag? Would that somehow cause it to not think it has enough room for another partition, as far as the Ubuntu install?

---

### Post by Quackers on 2011-08-20
Free space which is within a partition cannot be used by Ubuntu. It must be free space outside any partition.
You can defrag Windows then, if you are using XP, shrink the partition using gparted from within the Ubuntu live cd/usb desktop.
When resized, you should restart Windows to make sure it's still happy.
You can then try installing Ubuntu again. You should then get the alongside option.

---

### Post by airspoon on 2011-08-20
Thanks, I'll give that a shot. It's defragging now. Why is it that I haven't had to do this on the two other machines that I have so far installed Ubuntu on? Both of those machines had the hard drives already taken by the windows partition.

Also, so I'm basically creating my own partition, is that right? I should shrink windows to the remainder of which I'll be putting towards Ubuntu?

As far as gparted, is that what I get to when click on 'something else' where the 'install along side' option should be?

Thanks!

---

### Post by Quackers on 2011-08-20
On your other systems did you use the Ubuntu installer to resize the pre-existing partition?
I would have expected the 11.04 installer to offer the "install alongside" option if there is only one partition on there at the moment. 
However, a previous version of the Ubuntu installer had problems with this and sometimes over-wrote the existing partition.
It is always a good idea to have backups to return to in case of a disaster!
It is possible that there is another problem with your setup. If this is the case it will hopefully be revealed.

Yes, you should shrink the C: partition by the amount of space that you want Ubuntu to use (making allowance for a swap partition also!)

---

### Post by airspoon on 2011-08-20
I wound up just swopping the drive and installing as a single boot. If I ever need to retrieve the files or programs, I'll just swap the drive again, as opposed to dual booting.

It is interesting to note however, that after swapping the drive (it had Win 2000 Pro) and installing on that drive, it did give me the option to install 'along side'. It looks like the actual hard-drive may have had something wrong with it, or maybe the anti-virus was preventing it somehow? Even after trying to use gparted on the other drive, it wouldn't allow to me to resize the partitions.

Anyway, I have Ubuntu up and working on that laptop as a single-boot and that's all that matters, I guess. Thanks for the prompt, patient and courteous help.

---

