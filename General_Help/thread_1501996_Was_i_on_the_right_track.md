---
title: "Was i on the right track"
date: 2010-06-05
forum: General Help
---

### Post by GreatKeyHunter on 2010-06-05
Hi, i been playing around with ubuntu for the past months on virtual PC.  I finally decided to install it on another Hard drive.   I loved it, with the full features activated on it.  Its super fast.  It is a night and day difference between windows xp and ubuntu 10.04 lts. 

I was trying to set up a duel boot, since my system would just go automatically to the master drive.  The last thing that i typed on the terminal was sudo update-grub2.  Then i rebooted and it brought me to a line that looks similar to this.
GNU GRUB version 1.97~beta4

[ Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device/file completions. ESC at any time exits. ]  
i tried typing linux (hd0,1)vmlinuz root=/dev/sdal but vmlinuz was not found. 
Then i tried booting from the install disk and it said that the hard drive that contained linux had a few errors, missing partitons and what not. (its true, its a used hard drive that i had problems before with and i magically got it running again)  
I'm planning on buying a new hard drive to get linux running again.  But basically all i want to know is if i was on the right track to setting up a duel boot.

---

### Post by wojox on 2010-06-05
Did you set up a [SoftwareRAID]("https://help.ubuntu.com/community/Installation/SoftwareRAID") ?

---

### Post by GreatKeyHunter on 2010-06-05
> **wojox said:**
> Did you set up a [SoftwareRAID]("https://help.ubuntu.com/community/Installation/SoftwareRAID") ?

no i didn't, when i installed it i disconnect my other 2 hard drives from it. i guess i should have, now that i am reading into it.

---

### Post by sites on 2010-06-05
You need to leave the Windows drive connected when you install linux so grub will configure properly.

---

### Post by GreatKeyHunter on 2010-06-05
> **sites said:**
> You need to leave the Windows drive connected when you install linux so grub will configure properly.
 
Thanks for the tip, i guess it was just fear of messing things up.  I will replace the hard drive, with linux in it thou.  Its not the first time it has stopped working before. I a way, i had nothing to loose.  But now i loved ubuntu so much that i got to buy a new hard drive now =)

---

