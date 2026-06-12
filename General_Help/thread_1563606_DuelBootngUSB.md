---
title: "DuelBootngUSB?"
date: 2010-08-29
forum: General Help
---

### Post by PromptSquirrel on 2010-08-29
Okay, first off I wanna just say I enjoy Linux. I finally found a way to install it on my USB(Which this thread is about) and I hope to use Linux for sometime. 

I found a way to get Linux on my eight gig USB drive(FAT32). After installing it, and running it everything was fine right? Yeah, I could shutdown the computer and it would restart(By restarting, I mean Ubuntu had to restart after updates.) Well I turned the computer off, and took out my USB. Nothing wrong, stuff's good. 

I leave for a party, and leave my parents with the computer.(Its a family computer, don't hate) They call me complaining it won't load Windows XP. Something'bout a grube rescue and they're old and can't read. You know how it is. 

Any ideas on what I did? I thought when I installed Linux on my USB all I had to do was select it from the BIOS and it would select it. Then once I was finished, It would automatically select my C drive and boot XP. 

Thanks for any comments, help, or critism. You guys can tell I'm new to this. Also if there is a thread like this already. Sorry, I'll delete this. 


Thanks x2

---

### Post by gordintoronto on 2010-08-29
[http://www.webtree.ca/windowsxp/repair_xp.htm#How%20to%20Repair%20the%20Boot%20Sector:](http://www.webtree.ca/windowsxp/repair_xp.htm#How%20to%20Repair%20the%20Boot%20Sector:) 

and look for "recovery console"

During the Ubuntu installation, there was a moment when an "advanced" option was offered, with no explanation about why you might choose it. It would have let you specify that Grub should go on the flash drive. It's a weakness in Ubuntu.

---

### Post by C.S.Cameron on 2010-08-29
As a temporary fix the folks computer should boot when the thumb drive is plugged in. you might have to press the shift key when starting up to get the grub menu.
It is best to unplug the internal hard drive when doing a Full install to USB. Even using the Advanced option grub2 will make problems.

gordintoronto option of using the emergency repair console and doing a fixmbr is easiest if you have an XP install disk, if not Google "ms-sys", it's a Linux based Windows boot fixer.

---

### Post by PromptSquirrel on 2010-08-29
Sadly, I don't have a XP recovery disk. 
Now this Windows boot fixer, It shouldn't screw with my C drive right?

I kinda wanna keep my car, instead of selling it off to replace a computer :P

---

### Post by techunit on 2010-08-29
Well find a windows recovery disk pretty much any should do just make sure it is the correct version. [Here is a link]("http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/") on what do after you get a disk. Important Start at the point where the windows install picture is shown and follow the instructions. Good luck.

---

### Post by C.S.Cameron on 2010-08-29
I am normally quite cautious but I used ms-sys after a lot of research and found that it worked as advertised.

---

