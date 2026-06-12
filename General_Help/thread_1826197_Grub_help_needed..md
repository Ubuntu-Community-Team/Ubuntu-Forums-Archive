---
title: "Grub help needed."
date: 2011-08-16
forum: General Help
---

### Post by lostdev on 2011-08-16
First off, just want to say hello. Secondly, I wasn't sure where to post this grub specific issue, so I went with general help. 

Using GRUB2.

I am making my own .mod file for grub2 and am having issues looping through the data on a partition. I am new to creating .mod file but not to programming. 

I have a couple of issues, but the main problem is that the documentation is a little sparse for grub2. That is to say, the commenting in the code isn't all that helpful and I am unable to find a sufficient example of what I'm trying to do. 

using the grub_partition_get_len(partition) function, It returns an astronomically huge number. Now, the api says it returns sector units but I don't know what a sector "unit" is .... is it a single sector on the disk? Each sector is 512 bytes, correct?

Any clarification you guys could provide on grub_partition_get_len or grub_disk_read's "offset" would be greatly appreciated. Perhaps pointing me to a good source of info on the grub functions would be sufficient. Thanks!

---

### Post by lostdev on 2011-08-16
So just to add some more info. My understanding of the sector unit is exactly 512 bytes. So grub_partition_get_len(part) should return sectors, and if I want the bytes, that's 512*returnValue ... But if this is correct, its claiming that my partition contains more than 80,000 terabytes of data ... which is not true.

---

### Post by lostdev on 2011-08-18
Incase anyone was curious, the problem was that the data (uint64) needed to be uint32 ... so I right shifted 32 bits and all is good. However, I am not sure that I should have to do this, I don't know if somewhere deep in grub the number was cast to 32 bits, or if I should be using the le_to_cpu32 commands or not.

---

### Post by grahammechanical on 2011-08-18
How about this as a place to start looking for help?

[https://lists.gnu.org/mailman/listinfo/help-grub]("https://lists.gnu.org/mailman/listinfo/help-grub")

Regards.

---

### Post by lostdev on 2011-08-18
> **grahammechanical said:**
> How about this as a place to start looking for help?

[https://lists.gnu.org/mailman/listinfo/help-grub]("https://lists.gnu.org/mailman/listinfo/help-grub")

Regards.

Thanks for the link, I'll take a look there for future grub issues.

---

### Post by MG&amp;TL on 2011-08-18
Or #grub on irc.freenode.net.

---

