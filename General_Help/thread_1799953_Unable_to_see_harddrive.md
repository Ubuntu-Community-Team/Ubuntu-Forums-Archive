---
title: "Unable to see harddrive"
date: 2011-07-08
forum: General Help
---

### Post by thaleon on 2011-07-08
Hello guys, 
I ran Windows on this computer but it decided it wanted to die on me yesterday, so right now I'm using a Ubuntu Live CD. I wanted to save my files before I install Ubuntu on this harddrive, but when I click on 'Computer', I can't see my harddrive. However, if I go to Disk Utility I am able to see the drive: Unknown (500GB) and Unknown (490GB). I cannot access any of the partitions, so I tried to mount them. When I do that, I get the message: 
"NTFS signature is missing.
Failed to mount '/dev/sda3': Invalid argument
The device '/dev/sda3' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?" 

The same goes with /sda1/ which kind of sucks. I also tried with /sda/ but it didn't work either. I should probably also mention that when I try to run the Ubuntu installer it shows my harddrive, but no partitions. 

Thanks, Thal.

---

### Post by TBABill on 2011-07-08
You could try to use DBAN to basically wipe it clean. I'd think then it should be recognized, but you'll have lost all your files. [http://www.dban.org/](http://www.dban.org/)

---

