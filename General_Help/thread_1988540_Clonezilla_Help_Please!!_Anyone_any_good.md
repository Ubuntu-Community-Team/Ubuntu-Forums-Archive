---
title: "Clonezilla Help Please!! Anyone any good?"
date: 2012-05-27
forum: General Help
---

### Post by listerdl on 2012-05-27
OK this is what I am trying to do....

I dual boot.

I want to make a copy of my 80 GIG ext4 Ubuntu 10.04.2 partition and then re-image that on a nice new clean 250 gig HDD.

Once I have re-imaged the partition onto the 250 GIG HDD I will extend the size of it so that if fills the entire drive....

I tried doing this but I failed (I cant remember the error message).

Is the above possible? Anyone foresee any problems?

Thanks!!

---

### Post by wilee-nilee on 2012-05-27
> **listerdl said:**
> OK this is what I am trying to do....

I dual boot.

I want to make a copy of my 80 GIG ext4 Ubuntu 10.04.2 partition and then re-image that on a nice new clean 250 gig HDD.

Once I have re-imaged the partition onto the 250 GIG HDD I will extend the size of it so that if fills the entire drive....

I tried doing this but I failed (I cant remember the error message).

Is the above possible? Anyone foresee any problems?

Thanks!!

Probably the partition numbers were different, from the save to the install.

If this is the case open the clone and change the partition on the img.gz.aa to the number on the one you are installing to just a right click rename just the number, and any others showing. Then open the text files and look for incorrect partition numbers, and change.

I would add that I always save partition by partition, as I always have several with different OS's when I use clonezilla.

---

### Post by listerdl on 2012-05-27
> **wilee-nilee said:**
> P..........change the partition on the img.gz.aa....

I get that by simply opening the backed-up folder right?

Thanks

---

### Post by wilee-nilee on 2012-05-27
> **listerdl said:**
> I get that by simply opening the backed-up folder right?

Thanks

Yeah, that is the place.

---

### Post by listerdl on 2012-05-27
BTW - i see your sig you have boot-repair - you should check out this - [http://www.supergrubdisk.org/rescatux/](http://www.supergrubdisk.org/rescatux/) 

I am sure you already know this but its really really good - its saved me so many times before...

---

### Post by listerdl on 2012-05-27
Going back to the thread - 

with clonezilla am I correct in saying that the partition number MUST be the same?

I mean, does the original partition number, say sdb1 - that must be sdb1 also on the new install drive?

Thanks

---

### Post by wilee-nilee on 2012-05-27
> **listerdl said:**
> Going back to the thread - 

with clonezilla am I correct in saying that the partition number MUST be the same?

I mean, does the original partition number, say sdb1 - that must be sdb1 also on the new install drive?

Thanks

I have not had a problem with sda to sdb, but only with the partition number being on the install end, being different, from the clone itself. You have to have a pre-formatted partition for delivery as far as I know.

So if my new partition that is waiting for the install is different, then the clone, I change the cloned to the one waiting.

I have never gone from drive to drive only saved to reinstall if the original breaks, so my experience is limited to that scenario.

There is a clonezilla channel on the IRC channel freenode as well.

As for supergrub I use just supergrub 2, but rescutux is a good one as well, I never really have to use it anymore though, I know what is in the mbr and which OS is controlling the boot, generally, lol.

---

