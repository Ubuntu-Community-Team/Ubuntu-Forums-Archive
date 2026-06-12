---
title: "Dual boot"
date: 2012-05-01
forum: General Help
---

### Post by JoeyZ on 2012-05-01
Hiya~

I got a question cause i tried to fix it myself but i searched everywhere cant find anything..
But ok here i go~ 
I installed a fresh clean version of Ubuntu 12.04 (dont think version really matters with this but anywho)
I want to be able to dual boot windows with Ubuntu as my default OS,
So i installed everything i got swap area i got /home /boot and / 
and 250 GB i tried leaving it as unallocated, and using it as NTFS 250 GB but formatted.. and EXT2..
But whenever i boot into the installation it says cannot winstall windows on the disk when i select the 250 GB.. for the side note ( i dont want to delete ubuntu i want to keep it cause i really like how ubuntu looks and i want to learn more about using it. )

---

### Post by sammiev on 2012-05-01
It's easier to install windows first then Ubuntu. It still can be done the way you are doing it but you will need to install grub2 afterwards.

---

### Post by Paqman on 2012-05-01
> **JoeyZ said:**
> 
So i installed everything i got swap area i got /home /boot and / 


That's probably your problem. If those are all primary partitions then you can't fit any more on the disk. There's a limit of four primary partitions per disk. Do you really need a separate /boot partition? It's only necessary for certain unusual types of setup.

If you have used up all four primary partitions then the easiest thing to do is probably to start from scratch. Install Windows, then install Ubuntu. If you want to keep the look and feel of your current Ubuntu install then just back up everything in /home. 

The Ubuntu installer is smart enough to sort it out for you automatically, but if you want to partition manually (for example if you want a separate /home) then I'd advise creating some or all of your Linux partitions inside an extended partition. By putting partitions inside an extended partition you can break the four partitions rule, as all the partitions inside the extended count as a single primary partition.

---

### Post by JoeyZ on 2012-05-01
Well i actually tried that but then it said i had a wrong system root or sth idk..
But uhm no i dont have to have the boot one on a diff partition lol.. so what is recommended to do? besides clean install windows then install ubuntu?
Btw u guys know how the top bar, when youre at the desktop,
if you hover your mouse over it you get file edit etc, is there a way to place that in the middle,
cuz now its actually crossing over Ubuntu desktop i dont like that XD.

---

### Post by JoeyZ on 2012-05-02
Soz for double post cant seem to edit it ._.
ive read allot of things about people trying to edit their top bar
isnt there just a reason to move it up a lil to the right.. ._.

---

### Post by Rebelli0us on 2012-05-02
Dual booting can be risky. You can install Ubuntu on the entire disk and then run all the Windowses you want as virtual machines. The advantage: you don't have to reboot because you can  run several OSes **simultaneously**. Here's my desktop running Ubu 10.10, Windows 2000 and Win 7.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=217097&stc=1&d=1335962134[/IMG]

---

### Post by grahammechanical on 2012-05-02
The top panel is doing what it is expected to do. This has been tested months ago before the upgraded versions of the Unity user interface were brought into the development version of 12.04.

The intention is for the Ubuntu community to develop what are called application indicators. Icons for these little programs appear in the top panel on the right and alongside the envelope icon and as more are added the middle section will start to get crowded.

I have an app indicators for changing the keyboard layout, for monitoring CPU, memory and downloads, and another for monitoring motherboard temperatures. If I run radio tray (internet radio station playing app) its app indicator goes into the top panel.

These app indicators on my system taken up one third of the top panel on my wide screen display.

Regards.

---

