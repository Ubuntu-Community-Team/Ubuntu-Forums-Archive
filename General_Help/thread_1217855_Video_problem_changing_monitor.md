---
title: "Video problem changing monitor"
date: 2009-07-20
forum: General Help
---

### Post by deserthowler on 2009-07-20
I work for WorldCare, a charity in Tucson, Arizona.  We receive donations of computers.  Some of these computers, the ones I deal with are higher end PIII computers.

My specific task is to refurbish these computers for sale in our charity store.  The store provides working computers for a reasonable price, about $20.  This money helps pay expenses of operation.  The project provides usable computers for low-income families.

We used Ubuntu and were quite happy with it.  We now are using Ubuntu 8.04 LTS (moved up from 7.10 when the repositories closed) and it is quite usable.  However we are having a major problem.  I set the computer up at my work area and move it to the store.  We find that using a different monitor than the one at my workstation causes the computer to turn into a birck in that the video becomes messed up and the computer is unusable.  

As people generally have their own monitors, this makes the computers completely unusable.  Is there an easy solution for changing monitors without bricking the computer?

Earl

---

### Post by clonne4crw on 2009-07-24
Changing monitors on the fly shouldn't be a problem. Have you tried 'zapping' the X Server (Ctrl-Alt-Bksp)? Sometimes it works for me when it comes to display issues.

---

### Post by deserthowler on 2009-07-26
> **clonne4crw said:**
> Changing monitors on the fly shouldn't be a problem. Have you tried 'zapping' the X Server (Ctrl-Alt-Bksp)? Sometimes it works for me when it comes to display issues.

I tried that.  It usually locks the keyboard and the mouse too.

Earl

---

### Post by deserthowler on 2009-07-28
> **clonne4crw said:**
>  Have you tried 'zapping' the X Server (Ctrl-Alt-Bksp)? 
 I haven't had a chance to look at 8.04 further but I found 9.04 has CTRL-ALT-BKSP disabled.  I had to go into xorg.conf and enable it by adding 

 Section "ServerFlags"
       Option          "DontZap"               "no"
EndSection

Now it works.  I'm investigating this further.

Earl

---

