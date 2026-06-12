---
title: "Updated ATI Driver Screen Resolution now to big for Monitor"
date: 2010-10-01
forum: General Help
---

### Post by norm7446 on 2010-10-01
I have just installed the most up-to-date ATI Driver. Which asked for a re-start after install to activate it properly. But when the PC restarted it loaded Ubuntu OK as I hear the Start-up Music, but the Screen Resolution is now set to high for my monitor. So all I get is a " Out of Frequency " report on the screen before it goes into standby mode, which is what it always did if I tried to set the resolution to high in Windows.

Can I sort this from the command line, or do I need to find another Screen that will take the new resolution

---

### Post by forestG on 2010-10-24
The file you are looking for to edit is the /etc/X11/xorg.conf file. Try editing it with vi editor or pico. If you have not used vi before better go for pico or nano editor. If they are not installed try sudo apt-get install pico (or nano). 

Anyway go through the file and try to change the resolution from there. The form of numbers you are looking for is for example 1280x1024.

---

### Post by norm7446 on 2010-10-25
Thanks Forest...

---

