---
title: "GParted won't let me enlarge my Ubuntu partition"
date: 2012-10-08
forum: General Help
---

### Post by BlueAZ on 2012-10-08
Yes, I have searched diligently, but haven't found the answer.  I have a 320 Gb HDD dedicated to my Ubuntu 11.10 installation.  This HD has never had any other OS on it.  At one point I was thinking about installing Windows on it too, so I went into GParted and successfully reduced the partition containing Ubuntu to around 76 Gb.  It runs fine there, but it also created a second 4Gb swap (I have 4 Gb RAM), & another 43 Gb partition.  I was confused, so left it alone.

Now I've gotten another HDD to put the Wish-I-didn't-need-it Windows on.  I'd like to expand my Ubuntu partition to use more of the disk it's on, but GParted won't let me.  I do this with the 11.10 live CD, with the Ubuntu disk unmounted.  I've also tried unmounting both swap's.  There is ample Unallocated Space right next to the Ubuntu partition.  But when I ask to 'Move/Resize Partition', it won't let me make it bigger than the 76 or so Gb.  It also won't let me move anything.  So I don't know if I'm doing something wrong or what?...:confused:

I'm attaching shots of what I see in GParted.  Please educate me!

---

### Post by agillator on 2012-10-08
First, what does gparted say the layout of the drive is (e.g. /dev/sda1 Ubuntu 76gb, unallocated x gb, /dev/sda2 . . . ). Second, when you click on the ubuntu partition and click to resize it, a dialog should open that asks about size before partition, new size, size following partition. What three values does it show before you try to enter anything?

---

### Post by oldfred on 2012-10-08
Use the paperclip icon in the edit panel above your message or in edit message go advanced to get the full edit menu panel.

Your gparted screenshots are not showing.

---

### Post by BlueAZ on 2012-10-09
Sorry I didn't get the attachments attached right -- they are now on the original question.  'Screenshot' shows what the GParted screen looks like when I open it.  'Screen2' shows what I get when I select 'Move/Resize' from the menu or R-click.

Thanks!

---

### Post by Cheesemill on 2012-10-09
You're having this problem because your extended partition is between sda1 and the unallocated space, you can only grow a partition if it is next to the free space with nothing in-between them.

First of all you need to turn off your swap partitions so that you can resize sda2, just right-click on them one at a time and select swapoff.

Then you need to shrink sda2 so that the unallocated space lies *outside* the extended partition (drag the left edge of sda2 as far right as possible).

You should now be able to resize sda1.

---

### Post by BlueAZ on 2012-10-09
Thank you Cheesemill!!  I followed your directions, using the live CD, and it worked perfectly!  I just didn't understand the Extended partition well enough.

I'm so grateful for helpful people like you -- have a wonderful day/evening/whatever!!

---

