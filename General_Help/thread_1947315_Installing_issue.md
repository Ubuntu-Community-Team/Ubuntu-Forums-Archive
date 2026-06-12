---
title: "Installing issue"
date: 2012-03-26
forum: General Help
---

### Post by luismgl on 2012-03-26
So I´m installing xubuntu on a laptop with 2 partition, one was where the system is and the other one is for my data that I want to save. so my question is, by chosing "replace windows 7 with Xubunut" will that also erase my data partion?

thanks

---

### Post by 2F4U on 2012-03-26
To be sure that your data partition is not touched, I would choose the custom partitioning, which I guess is named something else. There you can define what partitions Ubuntu should use, you can delete and create partitions.

---

### Post by luismgl on 2012-03-26
thank you for your answer.
The new option is now called "something else" I´ve tried that but its a bit confusing. I can identify where my data and windows are, but I'm not really sure what to do from there. 
I though I should delete the partition where windows is, later add a new partition, select it as primary with the remaining size of the disk and use it as Ext4 journaling file system. Im not sure what mount point I should use, I though I would use root (/) just.

are these steps ok?

---

### Post by luismgl on 2012-03-26
solved!

---

### Post by 2F4U on 2012-03-26
Thats right, either logical or primary is fine. In my experience it doesn't matter too much whether it is in the beginning or somewhere else. There certainly are very subtle difference (the beginning of the hard drive is usually a bit faster than the areas towards the end), but in real day computing I never found much difference. If you have enough RAM, it only rarely uses the swap area (I am aiming to have enough RAM so that the OS doesn't have to use swap, since the hdd is by magnitudes slower than RAM).

---

### Post by luismgl on 2012-03-26
Ive read that if you do use several HDD you should have the swap area in the beginning, although I can't prove if this is true of not. I have 2Gb of ram, so I used a total of 4Gb of swap area.
I can't say that I am fully satisfied with this OS, sometimes there is a lag when choosing options in programs like music player. I don't think it has anything to do with lack of memory although I can't shake the feeling it has something to do with the desktop environment as this is my fist time with XDE after moving from Unity on Ubuntu

---

