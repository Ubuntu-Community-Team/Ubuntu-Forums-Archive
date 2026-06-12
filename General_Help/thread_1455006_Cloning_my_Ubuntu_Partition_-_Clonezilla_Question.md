---
title: "Cloning my Ubuntu Partition - Clonezilla Question"
date: 2010-04-15
forum: General Help
---

### Post by empty_spaces on 2010-04-15
I was planning to use Clonezilla LiveCD to clone **only** the Ubuntu partition on my laptop. I got to the stage where it asks for a name for the cloned image. At this point, it was not clear whether it would clone my whole hard drive or just my specific Ubuntu partition. This matters because the external drive where I would store the image probably does not have enough space for the whole hard drive.

So if I keep going further, will it ask me to specify a partition, or just clone the whole disk?

Thanks

---

### Post by Quarkrad on 2010-04-15
Providing you have selected the option to clone a partition rater than the whole drive (this is an early option) - yes go ahead, it works fine.  I use it myself - the only annoyance I have is that Clonezilla does not backup/restore Grub (I dual boot winXP) so after re-installing you do not have access to your Ubuntu partition!  You have to manually re-install Grub (2) which in my experience is a pain.  I have tied numerous methods, sometimes one of them works sometimes not - very frustrating.  The irony is that the Clonezilla bit works OK.

---

### Post by empty_spaces on 2010-04-15
Thanks for the reply.
The attached screenshot is the only screen I remember where it asked about the disk or the partitions. 
I believe I chose the second option (saveparts), where although it says "save_local_partitions_as_an_image", it does not let me specify which one.

Did you mean this screen? 

Thanks.

---

### Post by Quarkrad on 2010-04-17
After selecting your 2nd option you should have another window which lets you select where you want the image (partition) to be saved to - I select **local_dev  Use local device (E.G.:hard drive, USB drive)**  because I what my partition image to be saved to 2nd HD on my system.  Having selected the above you just need to follow the screens.  What I found strange at first (although not after a few clones) is that you have to specify where you want the image saved to first and then you select the partition (in the form of sda1, sda 2, etc) you want to clone.

You need to identify the name (in the form of sda1, sda2, etc) of the partition you want to clone before you start.  You can do this using System, Admin, Gparted.

Just press a few more Clonezilla screens and you will work out how it works.  Don't worry - there is a cancel button/option on most windows so you can always 'bail-out' any time if you make a mistake.

---

### Post by empty_spaces on 2010-04-17
Awesome. Thanks for the detailed reply.

---

