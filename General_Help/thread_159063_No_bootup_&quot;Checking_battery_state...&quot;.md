---
title: "No bootup &quot;Checking battery state...&quot;"
date: 2006-04-12
forum: General Help
---

### Post by Mathias-K on 2006-04-12
Yesterday the LAN party i held at my place for some of my gaming friends ended. Of course, for flawless playing and setup of the newest games, this meant that i had to take out my Kubuntu hard drive and put in a clean drive for installing Windows XP. 

Today i tried putting back my Kubuntu drive as a slave to my Windows XP drive. That went horribly as i couldn't even boot Kubuntu. I got a message that /dev/hda1 did not exist.

That message was nowhere near helpful, but i figured it was because my IDE drives and cables were not configured exactly as before, so i did that. Then the Kubuntu splash came, and as usual when the computer has been moved, it took ages (5-6 minutes) trying to find the internet connection, eventually abandoning it to continue. This is where my problem comes in.

When the install comes to "Checking battery state...", it just does not come any further. I have waited for 25 minutes now, and that's more than the usual slow Kubuntu startup.

My specs are:
Kubuntu Breezy i386 kernel 2.6.12 i think, KDE 3.5.2
Athlon 64 3000+
ASRock 939Dual-SATA2
and so on..

Any suggestions? 

[SIZE="2"]PS:
Loving the Ubuntu community and my Kubuntu system, right now i feel kinda sad that it is just so utterly unreliable. As a side question, is this something that could be different if i changed to SUSE or another distro?[/SIZE]

---

### Post by Mathias-K on 2006-04-12
I must admit that i'm used to getting answers around here. Is there any other place that i can go to in search for a solution to this?

---

### Post by jonnymccullagh on 2006-04-12
This happened to me also a few days ago while trying to install kubuntu 5.10 - after a web search I put it down to the nvidia graphics drivers I had installed (via Automatix) for the nvidia card in the new machine.

Since it was a new machine and new install I took the graphics card out and re-installed - using the on-board graphics - that is why I held off on replying to you as I didn't think I could be of any help.

Did you make any changes to your Graphics Card?
(I probably won't be able to follow this up with anything useful but since no one else is replying to you)
All The Best,
jonny

---

### Post by Mathias-K on 2006-04-12
Well thanks for letting me know that i wasn't the only one with this problem :)

[QUOTE=jonnymccullagh]Did you make any changes to your Graphics Card?
(I probably won't be able to follow this up with anything useful but since no one else is replying to you)
All The Best,
jonny[/QUOTE]

I just had some days of Windows XP usage. The graphics card was submitted to proper XP display drivers and some heavy gaming, but that's all. Searching for it doesn't seem to help much..

---

### Post by Mathias-K on 2006-04-14
The problem was somewhat solved by a round of   [FONT="Courier New"][SIZE="2"]sudo dpkg-reconfigure xserver-xorg[/SIZE][/FONT]  in the console mode when booting up (CTRL ALT F1) and changing my display driver from nv to vesa.

I think there is quite a problem here. How would a new Kubuntu user know that if he got the error? What about at least giving him a suggestion on what to do?

---

