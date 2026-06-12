---
title: "Problem copying data to a USB drive"
date: 2012-06-20
forum: General Help
---

### Post by madhangc on 2012-06-20
Hi, 

I am using Kubuntu (12.0.4) 64 bit on a Thinkpad Edge E420. I have a question and a problem:

1. When I switch on the laptop, after the BIOS check I am not able to see the screen that shows the list of OS options to choose. Can someone help me how to enable it. 

2. When I copy data from my HDD to a USB drive the copy process of very slow and it slows down the OS. I am not able to do any work till the copy ends. 

Any ideas or solutions on this would be greatly appreciated. 

Thanks in advance, 
-Madhan

---

### Post by Bucky Ball on 2012-06-20
Welcome.

Hitting shift after BIOS gets you to the menu. If this fails, try escape (it used to be that).

When you get to the menu run the recovery kernel (second one down) and see if that tells you anything.

---

### Post by madhangc on 2012-06-21
Hi Bucky,

Thanks for helping me out. 

I tried to do escape after the bios screen and it is showing the list of OS options. I tried the recovery mode and not able to find any clue. 

Any help on the USB data copy problem would be greatly appreciated. Also, when we tried to open the copied movie on a Windows 7 computer, the video player says the file is corrupted. Any idea why this is happening?

Thanks,
-Madhan

---

### Post by dcottingham on 2012-06-21
What you say about the USB drive makes me suspect that the drive has a hardware problem. During the copy you might try "tail /var/log/syslog" and see if you're logging any complaints about the drive. You also might try opening the movie on your Linux system. Or putting some shorter file on there -- for example, a short text file -- and see if it looks ok.

---

### Post by manfromthezoo on 2012-06-21
You could also run Disk Utility with the drive connected.

Check out any SMART errors reported for disks - bad sectors, etc.

---

### Post by madhangc on 2012-06-21
> **dcottingham said:**
> What you say about the USB drive makes me suspect that the drive has a hardware problem. During the copy you might try "tail /var/log/syslog" and see if you're logging any complaints about the drive. You also might try opening the movie on your Linux system. Or putting some shorter file on there -- for example, a short text file -- and see if it looks ok.


Thanks for your response. I tried to check the system log while the content is getting copied and not able to see any errors. The movie is playing good is linux. I tried to copy a different movie and it is playing good in Windows 7.  

But the kubuntu gets very slow when the copy happens from the laptop to the USB drive. I am not able to do any other work till the copy gets over. Any ideas on this?

Thanks for all your help!

---

### Post by madhangc on 2012-06-21
> **manfromthezoo said:**
> You could also run Disk Utility with the drive connected.

Check out any SMART errors reported for disks - bad sectors, etc.

Thanks for your thoughts. I will try this and let you know what I find.

---

### Post by dcottingham on 2012-06-22
I'm running low on ideas, but I do wonder if you have anything else plugged into another USB port when you're experiencing a slow USB copy. If so, you might trying unplugging the other things and seeing if the problem persists.

---

### Post by madhangc on 2012-06-29
> **dcottingham said:**
> I'm running low on ideas, but I do wonder if you have anything else plugged into another USB port when you're experiencing a slow USB copy. If so, you might trying unplugging the other things and seeing if the problem persists.

Thanks for your thoughts. I think there is some problem with the USB drive itself and that is the reason why I the contents were not copied properly. 

But the OS gets very slow when items are copied to any USB drive. I checked the logs and not able to fine any clue. Not sure what the problem might be.

---

