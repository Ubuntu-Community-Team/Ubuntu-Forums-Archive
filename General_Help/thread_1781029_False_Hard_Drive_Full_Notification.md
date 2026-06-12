---
title: "False Hard Drive Full Notification"
date: 2011-06-12
forum: General Help
---

### Post by Fsmv on 2011-06-12
I have added no data to my hard drive in the last few days. I saw a notification saying I had only 1.8Gb left on my drive. Shortly after I dismissed it and ran: ```
sudo apt-get clean
``` like the notification suggested. Then, another poped up. Now it said I have 0 bytes left.

So, I opened the disk usage analizer and the data seemed normal, and not my full drive size. It still was saying I have no space so I checked the properties widow for / . It said / contained 128TB of data and the file counter showed no signs of stopping after a few minutes. Obviously my drive is not 128TB in fact it's only 500GB. Also the disk manager program (system volume information?) Said it has 28 bad sectors.

What could cause this and how can I fix it? Is my drive failing?

---

### Post by Fsmv on 2011-06-13
After further testing I've found the disk usage analyzer says I have 127.1GB in my hom folder but when I check the properties window in my home folder it only says 23.6 GB the correct value. I'm afraid the disk is failing. I guess I'll mirror it to my external drive.

---

### Post by lisati on 2011-06-13
Have you emptied the trash?

---

### Post by Fsmv on 2011-06-13
> **lisati said:**
> Have you emptied the trash?

Of course I have. There's about 100 GB less data than ubuntu thinks there is.

---

### Post by Fsmv on 2011-06-14
After messing with the partition table it has the correct amount for free space but it still says I have 128.2 TB on the drive. Apparently there are also some parts unreadable too. How does the computer know how large a drive is? Is it a piece of data on the drive that could be in a bad sector? Anyway here's a screen shot of what I'm talking about. Is it possible to find out which parts are unreadable (I ran this as root so it's not a permissions issue).[IMG]http://i53.tinypic.com/2uh7a89.png[/IMG]
And here is what the disk usage analyzer has to say:
[IMG]http://i52.tinypic.com/oqeyo3.png[/IMG]

---

### Post by goosenipples on 2012-09-14
I actually have the same probem right now. 
 
I have a 160GB RAID 1 array with my OS and a 4TB software RAID6 array of 6 x 1TB drives and I just upgraded from using 10.10 server (ran great forever and I wanted to stick with it) with some desktop components added for GUI....I was TRYING to just update 10.10 but not upgrade to 11.04 and I was really like paying attention to what I was doing, making sure I wasn't upGRADing put upDATing and somehow it upgraded to the new 11.04 and made me very angry it upgraded and terrified that I had to restart. I had to manually start my RAID array which always freaks me out, but I digress. 
 
I turned on my monitor to a disk warning popup that I had very little space left. Closed it another popped up saying I had none left. Disk Utility shows full Disk Analyzer shows 128TB and climbing but if you drill down and sort by size and such the numbers don't add up to even full use of the 160GB 
 
Also, Firefox was working ok for a week or two since the upgrade but I just tried to open it and it's crashing over and over. Just did an uninstall and reinstall to no effect. Now getting: "your firefox profile is unavailable. It may be missing or unavailable"
 
Do you, or did you have any of these symptoms during the time of your situation?
 
Screens on request. 
 
Chris

---

### Post by Fsmv on 2012-09-14
> **goosenipples said:**
> I actually have the same probem right now. 
...
Do you, or did you have any of these symptoms during the time of your situation?
 
Screens on request. 
 
Chris

I never found a solution, I think I would have posted it here. I don't remember what I did, but I'm sure it wasn't a hardware problem.

I either just re-installed Ubuntu or quit using it and installed Debian. Maybe try checking your drives with a live CD and back them up then re-install. Sorry I can't help much.

---

