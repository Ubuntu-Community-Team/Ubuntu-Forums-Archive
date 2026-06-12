---
title: "Not able to install side-by-side with W7"
date: 2011-02-20
forum: General Help
---

### Post by umwhat on 2011-02-20
I'm on a friend's latptop and he asked me if I could install Ubuntu while I have it. His laptop is ridiculously slow and the audio is slow and choppy when on Windows 7, but when on Ubuntu, everything runs perfectly. Problem is; there's no scale for selecting the amount I want to partition. There isn't even an option for dual-booting. I don't know much about computers, other than basic installation, so I don't want to go and ruin his laptop. 

This ([http://i53.tinypic.com/o7n3o3.png](http://i53.tinypic.com/o7n3o3.png)) is all I see when I get to the partitioning.

---

### Post by grahammechanical on 2011-02-20
Do not take me as someone who knows what he is talking about on this subject but, I would guess that the option to install side by side is great when there is only one existing operating system on the hard disc. How is the poor little partitioner program going to install side by side when there are already two operating systems on the disc?

I think that this is why the option to install side by side is not offered. It would be impossible to do.

My guess is that you would need to select Specify Partitions Manually (Advanced) and reduce the size of the windows partitions to create space for Ubuntu. You did not enlarge the dialog box to full screen so we cannot see how large the hard disc is and how much space is being given over to the two Windows installations. So, cannot advise you on that.

Some say that you should use the Windows tools to partition the hard disc.

Your friend needs to think seriously about the usefulness of having Windows 7 on an underspecified machine.

Regards.

---

### Post by Frogs Hair on 2011-02-20
I set the size of my Ubuntu partition from windows disk management prior to installation. When get to the partition part of the Ubuntu installation it's ready to go. I also dual boot and have not tried a triple boot.

---

### Post by CHRSB on 2011-02-20
A few questions. 
How much space is free on his drive? 
What is that sda3 partition?
Did he update his Vista to Windows 7?
Does he have a back up of his data?
Does he have Windows 7 Install disks?

It looks like he upgraded his Vista install to Windows 7. Which is probably why his Windows 7 install sucks. And he probably does not have enough space left on his disk as well. Clock on the Computer icon see how full his drive is. And get the app CCleaner if it seems full and to clean out the crud.

Note that installing Ubuntu on this drive will probably make the last partition (the vista system restore partition I am assuming) useless. But if he has the Windows 7 install disks you can feel free to delete that partition. In fact, you could just do a clean install of Windows 7, but that is not what we want. :) 

You should tell your friend, there is a chance you could loose his data, so back it up and be prepared with his drivers as well for a reinstall of windows 7. You could download clonezilla and make an image of his drive and  wipe the drive and install Ubuntu. (Windows 7 comes with an excellent back up app as well. But clonezilla is a lot faster.)

First, boot into windows 7 and disable system restore, hibernation, and turn off system paging. (That will free up about 10GB plus of space) You can restart these later, this just makes it quicker to resize the drive and defragment the drive. So, yeah, next defragment the drive.

Boot back into ubuntu and look for Gparted in the System > administration section. I would like to see a screen shot of that actually. It will shhow muc 

If that last 30GB (sda3) is the restore partition for vista feel free to delete it. Then you can resize the sda2 partition.

Well, a little taste to get you thinking. But he needs a reinstall of something, trust me on this, been fixing  peoples gummed up machines for years and it is always the best option  for happy customers.

---

### Post by dver on 2011-02-20
apart from the advices given above i would also advice to follow these steps


- make a partition using window7 partition function 

now this will be the partition you will load ubuntu on

- now begin installing ubuntu - reach till the step of manual partitioning

- select  - you prefer manual partion

- scroll down to select the partition that you prepared in windows for ubuntu. remember that ubuntu shows partitions in different way. so remember the size of the partion 


- select this partition and click on change

this will take you to probably - edit a parttion page

- here in the window where size is written - write size in mb of double the size of your ram - and from another window - use it as the swap area and say ok. leave the mount point as blank


(this process reduces this size from the partition you kept for ubuntu)

- now again go and select the remaining partition (should be of good size - I plan the partion in such a way that after making the swap partion i have minimum 30 gb left in my drive to work efficiently and upgrade easily in the future)

- so now you select the remaining partition area - again click on add - you are taken again to edit a partition window - let the size remain as it is - just select this area  

use it as ext4 journaling system

- then go to mount point and select symbol / as your mount point

now click ok


- now again select this portion from the list and click on install now

- these steps have worked for me till now. 

though normally i have never lost any data on the windows partion but it is advisable to keep a backup of your data before you load ubuntu on the same drive.

---

