---
title: "Ubuntu 9.10 on an Asus 1001P netbook"
date: 2010-04-11
forum: General Help
---

### Post by welshmike on 2010-04-11
I'm about to take delivery of an Asus 1001P netbook with XP installed on it.
My current laptop runs dual boot Ubuntu 9.10 and XP and I'm very happy running Ubuntu as my regular system.

I will want to install Ubuntu 9.10 on the netbook.
What experience does the team have of running dual boot Ubuntu 9.10 and XP on an Asus 1001P netbook or any similar Asus netbook?
Instead of (the full) Ubuntu 9.10 that I like so much should I consider netbook remix?

Advice from the team would be most welcome. Thank you.

Regards
Mike

---

### Post by Klump on 2010-04-11
> **welshmike said:**
> 
Instead of (the full) Ubuntu 9.10 that I like so much should I consider netbook remix?

Only unless you feel lack of screen space. From my own experience - I don't think you will gain better performance. Instead, you could try XFCE desktop, it should be lighter (or even LXDE). On my netbook (Eee PC 1000) I use Ubuntu without any problems though I have replaced nautilus with thunar (which comes as default file manager in XFCE) and metacity with openbox. So, with few tweaks here and there you can make your little machine into a beast :)

---

### Post by welshmike on 2010-04-11
Klump,

Thanks for the info. I'll report back on my experience in a week or so.

Mike

---

### Post by welshmike on 2010-04-17
I promised feedback.
My netbook arrived with its hard drive partitioned as shown in the screenshot below (taken using Gparted running from an Ubuntu 9.10 live USB stick.
1. I ran Acronis True Image on XP and created a true image backup of the hard drive.
2. I used Windows XP Norton Partition Magic to adjust the partitions on the hard drive as follows:
- resized sda1, the XP partition, to 20GB, 
- resized sda2, don't know what this is for as it was empty, to 40GB and moved it to follow sda1
- formatted the free space created by the resizing above to ext3 ready for an Ubuntu install.
3. I then installed Ubuntu.
All went well. The GRUB menu was shown on boot. Ubuntu boots and runs OK, XP boots and runs OK. The PE labelled FAT32 partition still provides factory restore. ASUS Express Gate works.
4. I ran Acronis True Image on XP and created a true image backup of the hard drive.
5. Now the puzzling stuff:
I'm not confident about resized partition sda2 as it is now shown as hidden with no partition letter as seen in XP. It was D: and I'm not able to assign a partition letter or use the partition in XP.
Partition sda3 previously having had no XP partition letter now has letter D:.

I need to work on this further.

Mike

[IMG]http://www.eacott.org.uk/Screenshot.png[/IMG]

---

### Post by welshmike on 2010-04-17
Further work.
I noticed that partitions sda1 to sda4 were all primary partitions.
Somehow in using Norton Partition Magic I changed one to logical so that the freed space could be made primary ext3 for Ubuntu install.
The big question now is.
What was sda2 for and what will happen if I delete it?

---

