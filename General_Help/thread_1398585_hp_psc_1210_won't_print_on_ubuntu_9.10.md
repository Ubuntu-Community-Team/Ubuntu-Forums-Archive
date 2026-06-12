---
title: "hp psc 1210 won't print on ubuntu 9.10"
date: 2010-02-04
forum: General Help
---

### Post by cim on 2010-02-04
it was a fresh install of the distro and i updated it using update manager. i plugged in the printer via usb and it recognizes it but the damn thing won't print for ****. i've looked on the forums for a solution and there's nothing there. one guy had the same problem as me but no one posted it so i'm here to revive that post. anyone got a solution for this? the test print works but it prints blank pages! wtf is going on? as advance as ubuntu is, printing shouldn't be a problem. this is an urgent matter and i'm sure other people out there has the same problem as me. please help!

---

### Post by Johndo1 on 2010-02-06
Click on: System
then click on Administration
Then click on Printing
Then in that window click on printer then click on enable. 

That fixed it for me.

---

### Post by Rocket99 on 2011-05-27
I too had the same problem with an HP PSC-1200 series printer / scanner, in this case with Ubuntu 10.04 Lucid.  I tried the setting from JohnDo1:[INDENT]"Click on: System, then click on Administration, then click on Printing, Then in that window click on printer then click on enable. " 
[/INDENT]but didn't work yet (but I left it "enabled").  

Then I looked in printer properties (system menu , administration, printing, select printer icon, printer options).  I saw that under "General" the printout mode was set to "Normal- color cartridge".  Under the "Printout Mode" heading below, it was set to "Controlled by 'printout mode'."

Solution:  Under "General" heading I selected printout mode to "Normal grayscale (Black Cartridge)" and then under the "Printout Mode" heading below, I forced it to use one of the black cartridge options (e.g. 300 dpi, Grayscale, Black Cartr.).  This combo worked.  

I'm not sure if the second change was necessary as I didn't try it both ways, but now I at least have black text printing.  I will have to test it to see if I can force color printing in the same way (have to wait as I'm out of color ink).

Just thought I'd document my experience in case it's useful to someone else.  :)

---

