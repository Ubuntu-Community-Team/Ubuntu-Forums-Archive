---
title: "Ubuntu/Win7 duel OS help"
date: 2011-01-11
forum: General Help
---

### Post by Cpierce on 2011-01-11
I run Ubuntu 10.04 on my main laptop. I have an extra laptop that also has 10.04 on it. I would like to do a duel system of 10.04 and win7 on this extra laptop. I have added Ubuntu to computers that already had windows installed. Ubuntu makes this pretty easy to do. But this is the reverse, and I am afraid that the windows installation will mess up my Ubuntu. 

Could someone walk me thru step-by-step what I would need to do ?

I believe I should use gparted and make a separate partition, then install Win7 to that partition, and then reconfigure grub ? Just need to know how to do this. 

Would appreciate any help.

---

### Post by Cpierce on 2011-01-11
I burnt a Gparted live CD and successfully resized my Ubuntu partition. I created a new partition #1 in NTFS format which I labeled C:  Hopefully, I have proceeded correctly. I assume that I just need to install Win7 to this new partition, but not sure how it will effect grub. I would like some step-by-step advice before I move any further. 

Please Help

---

### Post by Cpierce on 2011-01-12
Well, I had to keep trying. I installed win7 on the new partition and it installed just fine. However, every time I booted the computer, it would boot on win7. I stuck my gparted live CD in, and saw that the win7 partition was flagged as "boot". I changed the "boot" flag to the Ubuntu partition. However, when I started the computer, I got a message that the operating system was missing. So now I believe that I need to reconfigure grub2 so I can select Ubuntu or win7. 

Would really appreciate some help.

---

### Post by FraggerMan on 2011-01-12
You don't need to do that, you can use the windows 7 boot manager. Just flag windows 7 as boot again, download EasyBCD [http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1). The rest should be pretty self explanatory. Just add ubuntu to the list of entry's by finding out the letter of the ubuntu partition and go to advanced and click write MBR and your done.

---

### Post by Cpierce on 2011-01-12
I figured it out. re-installed grub from liveCD with info from here:

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

works as it should. Marking this as solved.

---

### Post by Cpierce on 2011-01-12
Hey FraggerMan, I appreciate the help. That actually looks like a good boot manager.

---

