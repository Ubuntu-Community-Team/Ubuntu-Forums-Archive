---
title: "Cant add any printers.."
date: 2010-03-24
forum: General Help
---

### Post by justin_3994 on 2010-03-24
ive have been using ubuntu for years and have never had any issues except now. I had a local HP laser jet added and multiple network printers added. my computer installed updates then rebooted and all my printers were gone and it wont allow me to add them back. the new button is grayed out and the menu option to add a new printer is also grayed out. please help..


[IMG]http://images.roflcopter.net/image/3921.jpeg[/IMG]

---

### Post by bobcollard on 2010-03-24
> **justin_3994 said:**
> ive have been using ubuntu for years and have never had any issues except now. I had a local HP laser jet added and multiple network printers added. my computer installed updates then rebooted and all my printers were gone and it wont allow me to add them back. the new button is grayed out and the menu option to add a new printer is also grayed out. please help..


[IMG]http://images.roflcopter.net/image/3921.jpeg[/IMG]
Couldn't help to notice the "Not Connected" message at the bottom of your screen shot.   That may be a clue.

---

### Post by justin_3994 on 2010-03-25
my local printer is connected just not recognized... it also isnt recognizing my netowork printers. i read some where on another thread that re installing cups will fix this so i did. after cups finished installing again it let me add all my network printers back and my local printer, but when i restarted they were all gone again and it was back to not letting me add anymore.

---

### Post by bobcollard on 2010-03-25
> **justin_3994 said:**
> my local printer is connected just not recognized... it also isnt recognizing my netowork printers. i read some where on another thread that re installing cups will fix this so i did. after cups finished installing again it let me add all my network printers back and my local printer, but when i restarted they were all gone again and it was back to not letting me add anymore.
How are they networked, wifi or hardwired?  Are you using a router, USB?

---

### Post by justin_3994 on 2010-03-25
my local printer is usb and my netowrk printers are at my school and those are hardwired....it kinda making me mad cause every time i need to print something i have to re isntall cups then add the ip of the printer again, browse the the plethora of drivers, then print...only to redo it all over again after i reboot

---

### Post by Morbius1 on 2010-03-25
Is the CUPS service running? The "Not Connected" may refer to the CUPS server not any attached printers.

Run the following in a Terminal: **sudo service cups status**

If it's not running, start it: **sudo service cups restart**

---

### Post by bobcollard on 2010-03-25
> **justin_3994 said:**
> my local printer is usb and my netowrk printers are at my school and those are hardwired....it kinda making me mad cause every time i need to print something i have to re isntall cups then add the ip of the printer again, browse the the plethora of drivers, then print...only to redo it all over again after i reboot
It's difficult.  You are using printers on different subnets connecting and disconnecting your computer and moving it.  Here is a how-to link with several good ideas.  I'm not sure cups alone will solve your problem.  Networking printers has always been a problem for IT people like me.  I've done it but I'm not there.
[http://www.ibiblio.org/pub/Linux/docs/HOWTO/other-formats/html_single/Printing-HOWTO.html](http://www.ibiblio.org/pub/Linux/docs/HOWTO/other-formats/html_single/Printing-HOWTO.html)

---

### Post by justin_3994 on 2010-03-25
netowrked printers alone i can live without those but i also cant add any local printers...unless i reinstall cups and even then once i reboot its gone

---

### Post by bobcollard on 2010-03-25
It could be that cups is not starting each time your reboot,  Do the following and add your printer, then reboot and see if it helps.
I found this on Google:
To solve your problem, simply add the following two commands BEFORE the  last line in /etc/rc.local  (Note:  You must edit rc.local as root.) 
 
At the command line: 
```
sudo gedit /etc/rc.local 
```add... 
sleep 20 
/etc/init.d/cups restart 
...before the last line... 
 
save the file 
restart the computer 
 
CUPS should start at each boot now.

**EDIT**: I forgot to tell you to reinstall cups first.

---

### Post by justin_3994 on 2010-03-25
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0
```  this is what pops up in the text editor when i run your command.....im not sure where to add the line

---

### Post by bobcollard on 2010-03-25
> **justin_3994 said:**
> ```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0
```  this is what pops up in the text editor when i run your command.....im not sure where to add the line
Add it above exit 0  The rest is just comments.  Looks like you may need to remove the comment (#) from the first and third lines

---

