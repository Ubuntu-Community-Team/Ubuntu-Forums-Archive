---
title: "Need help recovering private data"
date: 2011-01-07
forum: General Help
---

### Post by SolidShake on 2011-01-07
Good day all!
Since recently I have installed windows (dont worry I will be back to ubuntu soon enough but I've ran into some trouble), I had installed windows on my main hard disk (I couldn't install windows on my 2nd hard disk for some reason). 
There were 2 partitions on the main hard disk, 1 which had all my data and another which had all the system fyles for ubuntu on it I believe. 
Now I deleted the small system fyle partition and installed windows over it thinking I'd have all my data on the other partition when I needed. 
But when I started up ubuntu with a live USB (I had made it prior to deinstalling ubuntu because I wanted to go back asap) and browsed my files, I noticed that I couldn't get to my private data anymore! :( 
The /home/user partition is still there but it only has a file in it which says something like "recover-private-data.desktop" but when I double click it (made it executable) it just pops up a terminal real fast and disappears. 
 
What do I do please help!!

---

### Post by gordintoronto on 2011-01-07
Is it possible that you are browsing the /home/user folder on the USB drive?

When you have booted from a USB drive, you need to click on "nnn GB file system" to get to the hard drive. (nnn is the number of GB for the partition.)

---

### Post by SolidShake on 2011-01-07
> **gordintoronto said:**
> Is it possible that you are browsing the /home/user folder on the USB drive?
 
When you have booted from a USB drive, you need to click on "nnn GB file system" to get to the hard drive. (nnn is the number of GB for the partition.)
 
Hey gordintoronto, thanks for the reply!
Yes I'm running it from a USB drive, made it with 'create live-cd' in ubuntu. I have mounted my hard drive and I can see my 'original' /home/user/ file on the hard drive but it is encrypted or something. I've noticed a .ecryptfs map in /home (i.e. /home/.ecryptfs) which is the same size as all of my data was. How can I get this back?

---

### Post by gordintoronto on 2011-01-07
Sorry, I have no idea. I do not encrypt data.

I think you should start a new thread, with a subject line of "recovering encrypted data" and mentioning encryption in the body of the message.

---

