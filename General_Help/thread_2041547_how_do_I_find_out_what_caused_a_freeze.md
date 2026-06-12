---
title: "how do I find out what caused a freeze"
date: 2012-08-12
forum: General Help
---

### Post by LLCoolJeff on 2012-08-12
After finally getting a startup script to work my computer completely froze a minute or two later (unsure if they are related)

the computer screen completely locked up, preventing me from moving any windows or getting any response, but the mouse still moved although it was stuck on the "hand"

I did a google search on my phone and couldn't find any way to fix this so I just had to nuke (power cycle) the machine. How can I find what caused this (in some kind of crash log?) and what should I try next time it happens?

I tried REISUB method by holding (alt+PrtSC and typing R+E+I+S+U+B) and nothing happened....

Thanks, I hope my problems end soon...

---

### Post by sienile on 2012-08-12
Found a site that lists all the various log files.

[http://www.cyberciti.biz/faq/ubuntu-linux-gnome-system-log-viewer/]("http://www.cyberciti.biz/faq/ubuntu-linux-gnome-system-log-viewer/")

---

### Post by marlow59 on 2012-08-12
Did you try to change the number (5) in the script that you created (if you are talking about the script you made to share screen or smth like that) and put a higher number in case X doesn't start completely before your script runs. if you are talking about another script, please add some additional informations such as the content of the script.

---

### Post by LLCoolJeff on 2012-08-12
> **marlow59 said:**
> Did you try to change the number (5) in the script that you created (if you are talking about the script you made to share screen or smth like that) and put a higher number in case X doesn't start completely before your script runs. if you are talking about another script, please add some additional informations such as the content of the script.

it is the script you speak of ([http://ubuntuforums.org/showthread.php?t=2041248](http://ubuntuforums.org/showthread.php?t=2041248)) although I highly doubt that is what caused the crash as I have logged out and in a few times since then and everything has been allright.

In fact the freeze was the only case I have ever had like this, and all I was doing was switching back and forth between email and firefox tabs and stuff like that

---

### Post by LLCoolJeff on 2012-08-12
ok it just happened again, this time it was no where near the login time...

I was playing around with an application called Jstock, it happened right when I clicked an option in a dropdown menu to change the style of stock chart when it just locked up. The same thing happened I could move the mouse but everything else was completely locked. 

I could not open up a terminal or anything with alt+f2.

How can I track down the cause of this?

---

### Post by 2F4U on 2012-08-13
Your first step should be to look into the system log file since it probably contains important information. The problem may be hardware related, so it could help to post information about your hardware. Additionally, since the locks seem to occur randomly, it may be a good idea to check the RAM installed in the machine by running memtest, for example from a liveCD.

---

### Post by ortermagic on 2012-08-13
LLCoolJeff
 
 I'm watching this post with interest since I have exactly the same problem.

---

### Post by LLCoolJeff on 2012-08-13
I have a hunch it is hardware related, I have ATI radeon 3200 mobile graphics card and its a pain in the *** because of various reasons, and it works like crap..

BTW I found the log file and I have a copy of it, but have no clue what I am looking for, I'm not even sure what time that happened so I just don't know where to look in there...

---

### Post by LLCoolJeff on 2012-08-13
> **ortermagic said:**
> LLCoolJeff
 
 I'm watching this post with interest since I have exactly the same problem.


what graphics hardware do you have?

---

### Post by ortermagic on 2012-08-13
Hi, I have ati radeon HD 6800  and I use the driver provided by precise, (after having experienced lots of problems with amdcccle which I am avoiding for now) Which driver are you using?

---

### Post by LLCoolJeff on 2012-08-13
> **LLCoolJeff said:**
> I have a hunch it is hardware related, I have ATI radeon 3200 mobile graphics card and its a pain in the *** because of various reasons, and it works like crap..

:confused:

---

### Post by sienile on 2012-08-13
If the problem is the ATI drivers, I recently upgraded mine to be able to play StarCraft 2. I have a thread concerning this saved in my bookmarks: [http://ubuntuforums.org/showthread.php?t=1878965]("http://ubuntuforums.org/showthread.php?t=1878965")

---

