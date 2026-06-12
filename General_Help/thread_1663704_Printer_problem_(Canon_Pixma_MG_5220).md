---
title: "Printer problem (Canon Pixma MG 5220)"
date: 2011-01-10
forum: General Help
---

### Post by Speedy_D on 2011-01-10
Hi,

I have a Canon Pixma MG 5220 set up as the default printer on my wife's laptop.  I am trying to set up printer on a network so that I can access it on my laptop (running Ubuntu 10.10).  Everything works fine from my wife's laptop.  I can select the printer through system-admin-printing-add printer - windows printer via samba.  when i click forward, the computer then tries to find drivers.  My problem is that my exact printer model is not on its predetermined list.  What options do I have to get over this hurdle? Can I select a model "close" to mine? Am I out of luck here?

---

### Post by Speedy_D on 2011-01-10
I am hoping that someone can help with my question.  Could anyone point to any resources to over come this issue?

---

### Post by dpmanthei on 2011-01-17
I have the same printer and problem.  Tried searching the web for a PPD file but couldn't get anywhere.  CUPS also doesn't have any MG series printers, so I'm not really able to choose a 'close' one.  

I'm a linux amateur...there's no way to use a Windows XP/7 driver right?  Like ndiswrapper for printers?

Ubuntu 10.04 LTS (32bit)
HP DV1000
Canon Pixma MG 5220 (connected via wifi)

Thanks!

---

### Post by drewster1829 on 2011-02-05
Does this thread help any?

[http://ubuntuforums.org/showthread.php?t=1588333]("http://ubuntuforums.org/showthread.php?t=1588333")

---

### Post by Remanifest on 2011-02-08
Thank you Drewster -- that thread helped me right away!

---

### Post by dpmanthei on 2011-03-07
[http://support-my.canon-asia.com/contents/MY/EN/0100301702.html](http://support-my.canon-asia.com/contents/MY/EN/0100301702.html)

Scroll to bottom, click download.  Extract, run the .sh in terminal, answer the simple questions.  Setup was flawless for me, I would suggest you have the printer configured and operating on the network ahead of time so the installer can detect it.

I did this in 10.10 and 10.04 with success for both, although I didn't even think to check wifi document scanning.

Cheers,
Dylan

Note: I should give credit for the link to walt.smith1960 at this thread: [http://ubuntuforums.org/showthread.php?t=1649084](http://ubuntuforums.org/showthread.php?t=1649084)
Thank you for your solution!

---

