---
title: "Copying data over before sending laptop for repair"
date: 2011-12-03
forum: General Help
---

### Post by AndyCinDallas on 2011-12-03
I have a Dell laptop (running Ubuntu 11.04) which is going back for repair under warranty as it doesn't turn on at all (7 beeps - indicates CPU or motherboard on the fritz).

Dell support indicated that they *might* have to wipe the HD, so I'm going to pull the drive out, connect it to my main box and see if I can copy my important files to my other PC (running Ubuntu 10.10 and XP).

Is there anything I should know beforehand about copying? I don't know a whole lot about permissions, etc, and I'm worried I won't be able to copy the files over from 1 drive to the other as a short search seems to show nightmare stories...

Any advice appreciated.

---

### Post by oldtimer7777 on 2011-12-03
I use Clonezilla all the time for this. Piece of cake.

[http://clonezilla.org/](http://clonezilla.org/)

> **AndyCinDallas said:**
> I have a Dell laptop (running Ubuntu 11.04) which is going back for repair under warranty as it doesn't turn on at all (7 beeps - indicates CPU or motherboard on the fritz).

Dell support indicated that they *might* have to wipe the HD, so I'm going to pull the drive out, connect it to my main box and see if I can copy my important files to my other PC (running Ubuntu 10.10 and XP).

Is there anything I should know beforehand about copying? I don't know a whole lot about permissions, etc, and I'm worried I won't be able to copy the files over from 1 drive to the other as a short search seems to show nightmare stories...

Any advice appreciated.

---

### Post by bluexrider on 2011-12-03
shouldn't be difficult, just remember to get those .HIDDEN files too

---

### Post by AndyCinDallas on 2011-12-03
Thank you, gents - we'll see how it goes tomorrow.

---

### Post by dcstar on 2011-12-03
> **AndyCinDallas said:**
> I have a Dell laptop (running Ubuntu 11.04) which is going back for repair under warranty as it doesn't turn on at all (7 beeps - indicates CPU or motherboard on the fritz).

Dell support indicated that they *might* have to wipe the HD, so I'm going to pull the drive out, connect it to my main box and see if I can copy my important files to my other PC (running Ubuntu 10.10 and XP).

Is there anything I should know beforehand about copying? I don't know a whole lot about permissions, etc, and I'm worried I won't be able to copy the files over from 1 drive to the other as a short search seems to show nightmare stories...

Any advice appreciated.

Use **gparted** to clone the whole partitions to some free space on another drive (as big as each partition).

Then you can reverse the process onto a new drive.

---

