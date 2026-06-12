---
title: "dd problem"
date: 2011-06-21
forum: General Help
---

### Post by luckbedamned on 2011-06-21
so i'm using dd to copy my harddrive to an external harddrive, and it's not going well

what i want is to be able to boot from the external and run the machine i have locally on other computers, using a usb interface.

what i did, is i made 3 partitions to the external drive, sdb1,2,and 5

1 being ext4, and the same size as the local harddrive
2 being extended, and 5 being swap

i did all this using gparted. So, the problem is the dd stops saying there's not enough space on sdb1 to complete the task, and when i try to mount it, it says that there's too many blocks. i used dmesg | tail to figure that out.

so, if anyone can help, i would really appreciate it.

thx in advance,
-dan

ps. sorry if this is the wrong forums to be posting this in, i just use ubuntufourms.org all the time and i usually dont have such an involved problem to solve... so... soz if that's the case! :P

---

### Post by jerrrys on 2011-06-21
i do not use DD, but wanted to say

for hdd to hdd clones i use [clonezilla]("http://clonezilla.org/").  "beginner mode" is all thats necessary to copy all partitions at once.

---

