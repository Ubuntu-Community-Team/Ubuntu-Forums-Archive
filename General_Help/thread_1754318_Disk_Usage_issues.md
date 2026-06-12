---
title: "Disk Usage issues"
date: 2011-05-09
forum: General Help
---

### Post by Mushu84 on 2011-05-09
I finally got Ubuntu installed and working, so far I'm like this OS enough that im thinking about wiping windows from it and making this a Ubuntu laptop!  The only thing that is really stopping me from doing so is the disk usage issues I've run into.

The partition that i have Ubuntu install on is 15GB, then I set the swap space to 5GB(I'm new to Linix and didn't quite know what a good disk size for the swap would be)  I haven't installed many apps, nor have i saved anything to this partition, I access my music and pictures from my Windows 7 file system by click on the icon for the 135 GB Filesytem and navigate through the Windows file system to the My Documents>My Pictures/My Music folders.

Every time i boot into Ubuntu I get a pop-up that says: 

This computer only has x.x MB disk space remaining.
You can free up disk space by removing unused programs or files, or by moving files to an external disk.

[IMG]http://desmond.yfrog.com/Himg640/scaled.php?tn=0&server=640&filename=lhbp.png&xsize=640&ysize=640[/IMG]

and gives me the options to "Examine..." or Ignore

When i click on "Examine..." it brings up the Disk Usage Analyzer and proceeds to scan my disk.

[IMG]http://desmond.yfrog.com/Himg614/scaled.php?tn=0&server=614&filename=smp0.png&xsize=640&ysize=640[/IMG]

I am at a loss for were my 15GBs went, the only thing i can think of is Ubuntu is saving the few things i have installed to the 4.0 GB Swap space or the 5.0 BG ext4.

[IMG]http://desmond.yfrog.com/Himg610/scaled.php?tn=0&server=610&filename=tb2.png&xsize=640&ysize=640[/IMG]

I do not know where the Extended 9.0 GB and the 4.0 GB Swap came from, I can only assume that Ubuntu made them during the install or Windows mucked up the disk partitioning!  But this issues is keeping me from installing the apps. i would like to be using.

Thnx,
The Ubuntu newb
~Mushu

---

### Post by Quackers on 2011-05-09
Can you post a screenshot of your gparted screen please?
You may need to install it first via synaptic package manager. If you don't have the space you can boot from the live cd/usb and run gparted from there. Any changes made will need to be made from there anyway.
It looks like Ubuntu has been installed to a 5GB partition (within the extended partition) rather than the 16GB partition.

---

### Post by Mushu84 on 2011-05-09
Thank you for you quick reply Quackers!  :3

Here is the screen shot of Gparted you requested: 

[IMG]http://desmond.yfrog.com/Himg616/scaled.php?tn=0&server=616&filename=4os3.png&xsize=640&ysize=640[/IMG]

---

### Post by Quackers on 2011-05-09
You're welcome.
Ubuntu has, in fact, been installed to sda5 rather than sda2, which it seems is what you intended. As sda2 is formatted as NTFS, Ubuntu would not install there (it needs a ext4 partition for root (/).
What I suggest is to boot from the live cd/usb and select "try ubuntu". Then from the live desktop launch gparted again and take the following steps.

First enquire as to what exactly is in /dev/sda2 (labelled "Ubuntu"). It currently shows 3GB in use. If there is anything you want on there please back it up to somewhere else.
Then I'll get back to you with more details :-)

---

### Post by Quackers on 2011-05-09
Ok
1) Right-click on the swap partition (/dev/sda6) and select "swapoff" (probably not necessary from the live cd, but good practice anyway)
2) Right-click on /dev/sda2 (your partition labelled as "Ubuntu") and delete this partition (obviously don't do this if you would like to keep sda2 for some reason) then click on the green tick mark in the toolbar to apply the change.
3)Right-click on the extended partition (sda3) and select Resize/Move and in the new box that pops up change "Free space preceding" to 0 and press enter. You should see the amount of MB used in the second box increase by about 16000MB. The third box should remain at 0. If this happens click on Resize/Move box. Then click on the green tick mark again in the toolbar to apply the change. I'm not sure but this could take some time to perform (if not, the next stage will do!)
4) Right-click on the sda5 partition and select Resize/Move. Then do the same again. ie change "Free space preceding" to 0 and press enter. The second box value should increase again whilst the third box value should remain at 0.
Click on Resize/Move box and then on the green tick mark in the toolbar to apply the change.
5) go and get a cup of tea and put your feet up. This will take an hour or maybe more.
6) When all is finished reboot and see if it boots ok.

---

### Post by Mushu84 on 2011-05-10
you sir, are amazing!  When i have some free time, I'll sit down and try this.  Once i'm done I'll update you with the results!  :3

Thnx
~Mushu

---

### Post by Quackers on 2011-05-10
You're welcome and good luck :-)

---

### Post by Mushu84 on 2011-05-11
Quackers!  You are the man!

Your suggestions did the trick, though admittedly step 5 had me worried, as you didn't specify what kind of tea I should make myself, but it seems my green tea worked just fine!  :D

Thanks again!
~Mushu

---

### Post by Quackers on 2011-05-12
Green tea is ok, if that's what you like :wink:
Glad things are good :-)

---

