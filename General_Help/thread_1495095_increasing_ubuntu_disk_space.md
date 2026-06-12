---
title: "increasing ubuntu disk space"
date: 2010-05-27
forum: General Help
---

### Post by mixint27 on 2010-05-27
I have lucid lynx installed on my laptop and win vista sp2.  When I installed ubuntu, I installed it side by side with win vista sp2.  Now i want to increase the size of the partition Ubuntu gave me (which gave me about 10 gigs when I first installed it.) Now how do i do this?  I have read other threads but im still kinda of confused. If someone could show me or direct me to thread that helps i would appreciate it.

Now, i know i need gparted which i have, but i dont know what to do.

I also want Ubuntu as my main OS on my laptop and leave vista with 10 gigs or so. I want to give Ubuntu all the space.

Again, please let me know what and how to do this.

Thanks!

---

### Post by drs305 on 2010-05-27
I wrote the following guide for expanding the Ubuntu system partition in response to a Jaunty bug. The second half of the first post contains the information you are probably looking for.

Backup your important data and defrag your Windows partition. Resizing the Windows partition is best done with a Windows app. Gparted can also do it from the LiveCD, which you will need to resize the / partition.

The guide wasn't written for the absolute newbie, so if you have questions, just ask them here. If you need help in deciding how to partition, a Gparted screenshot would be helpful.

[Expanding an Ubuntu System Partition]("http://ubuntuforums.org/showthread.php?t=1219270")

---

### Post by linuxman94 on 2010-05-27
First, you are going to need to boot of the live cd.  Once in the live CD, follow these steps.

1. Open gparted 
2. Right click on the windows partiton on choose 'Resize/Move'
3. Lower the size by how much more space you want on the ubuntu drive.  You can use the slider at the top to do this.
4. Click resize.
5. do the same for the ubuntu partition, but instead of lowering the space, increase it to fill the rest of the free space available.
5. Next click the 'apply' button at the top and wait for it to finish.

I would advise baking up important data that you don't want to loose before you do this.

---

### Post by mixint27 on 2010-05-27
ok here are the screen shots...

[ATTACH]158475[/ATTACH]

[ATTACH]158476[/ATTACH]


[IMG]file:///home/ubuntu/Desktop/Screenshot-Resize-Move%20-dev-sda5.png[/IMG]


How do you go about doing step 5?

Thank you!

---

### Post by drs305 on 2010-05-28
Your third screenshot didn't come through. Based on what I see from the others, here is what you need to do:

1, Unmount the swap partition - sda6. Even with the LiveCD, swap must be turned off (no key icon beside the partition). Highlight the swap partition, then Partition, Swapoff from the menu. sda3 and sda5 should not have 'key' icons beside them.

2. Expand the extended partition - sda3. This is the light blue-bordered partition. Drag the edge all the way to the left to incorporate all the unallocated space. If you want to use the menu instead of trying to get the mouse exactly on the blue border, highlight sda3 in the lower section, then Partition, Resize.

3. Expand the Ubuntu partition - sda5 - by dragging the left edge all the way to the left. 

4. Once you have done these steps, press the green Apply icon.

---

### Post by mixint27 on 2010-05-30
Thank you so much!!

---

### Post by drs305 on 2010-05-30
You are welcome.   :-)

If you fixed the problem, it helps if you mark the post "SOLVED" via the "Thread Tools" link at the top right of the first post. It allows helpers to concentrate on unresolved issues and may point others with similar problems to useful threads.

---

