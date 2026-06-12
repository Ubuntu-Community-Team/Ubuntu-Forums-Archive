---
title: "how to make USB devices visible in virtualbox..."
date: 2010-08-31
forum: General Help
---

### Post by badbradmx on 2010-08-31
i cant seem to find an option for this. im trying out mint and want to play music and videos but they are on a USB which i cant access. any ideas?

---

### Post by silverglade00 on 2010-08-31
You most likely need to install the one from the virtualbox website. They have a version with USB support and a different license. You want the Personal Use and Evaluation version.

---

### Post by badbradmx on 2010-08-31
> **silverglade00 said:**
> You most likely need to install the one from the virtualbox website. They have a version with USB support and a different license. You want the Personal Use and Evaluation version.

how do i install the non free version?

---

### Post by howefield on 2010-08-31
Click on the relevant link for your version of Ubuntu.

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

You may need to uninstall the version that you already have, using Synaptic Package Manager.

---

### Post by bodhi.zazen on 2010-08-31
he virtualbox user manual is almost manditory reading as virtualization can be complicated

[http://www.virtualbox.org/wiki/Downloads#manual](http://www.virtualbox.org/wiki/Downloads#manual)

IMO the manual is well written. You do not need to read it all, just skip to the relevant sections.

---

### Post by badbradmx on 2010-08-31
thanks guys, il have a read up to make sure i get this right, not been a linux user for that long so im still learning, il post my results as and when i get some. but for now, sleep, night all

---

### Post by DavidOfLondon on 2010-08-31
I seriously recommend just creating a live usb bootable iso image using unetbootin.

I did this for using Backtrack 4 and it is excellent. 

Get a 8Gb USB, download Unetbootin (windows or Linux version available), make your bootable iso of the operating system you want and off you go. Once you go into the BIOS to set "boot from USB" options it's all plain sailing. Using virtual machines to get anything done for real just becomes a real pain in the butt when they start crashing, bugging, sucking your ram out the door...

Live USB bootable is a much better option and you'll be able to use the USB memory stick easily.

If you have any questions send me a private message - this thing isn't sending me notifications.

---

### Post by badbradmx on 2010-09-01
> **DavidOfLondon said:**
> I seriously recommend just creating a live usb bootable iso image using unetbootin.
 
I did this for using Backtrack 4 and it is excellent. 
 
Get a 8Gb USB, download Unetbootin (windows or Linux version available), make your bootable iso of the operating system you want and off you go. Once you go into the BIOS to set "boot from USB" options it's all plain sailing. Using virtual machines to get anything done for real just becomes a real pain in the butt when they start crashing, bugging, sucking your ram out the door...
 
Live USB bootable is a much better option and you'll be able to use the USB memory stick easily.
 
If you have any questions send me a private message - this thing isn't sending me notifications.
 
ive tried creating a bootable drive but evertime i do it wont boot but il try the program you mentioned and hopefully with better luck. 
 
on a side note im currently around a mates fixing his windows PC, bloody thing. this is where i appreciate the security in linux distros

---

### Post by badbradmx on 2010-09-01
ok the program works a treat i now have a bootable thumb drive with mint on it, great, but, as you'd expect i have a problem.

im talking to you from Mint right now, but i get "boot error" when trying to boot from it on my mates desktop. its a dell inspiron 530. any ideas? or should i start a new thread regarding that aspect

---

### Post by drdanielfc on 2010-09-01
if ur still trying for virtualbox you need to join the VirtualBox user group along with using the proprietary VBox on their website as mentioned above

---

### Post by badbradmx on 2010-09-02
> **drdanielfc said:**
> if ur still trying for virtualbox you need to join the VirtualBox user group along with using the proprietary VBox on their website as mentioned above
ive given up on the non-free vbox, for now. boot from the USB has everything enabled so it works for me other than the fact the desktop gets a boot error when trying to boot from it

---

### Post by ProNux on 2010-09-02
The free version of virtualbox does not support USB as far as I know.  So the most practical solution is to use the BETA version (preferably the newest BETA) downloadable on the link below.

[http://download.virtualbox.org/virtualbox/](http://download.virtualbox.org/virtualbox/)

This worked for my USB camera.  Good luck!

---

### Post by badbradmx on 2010-09-02
> **ProNux said:**
> The free version of virtualbox does not support USB as far as I know.  So the most practical solution is to use the BETA version (preferably the newest BETA) downloadable on the link below.

[http://download.virtualbox.org/virtualbox/](http://download.virtualbox.org/virtualbox/)

This worked for my USB camera.  Good luck!

yeah i know but im just gonna create bootable thumb drives as then the system is only running one OS. but its ok for trying out the basic, everday functions

all the help has been well received and bookmarks made so il have reference to them at a later date, but for now i need the DAMN DESKTOP TO BOOT FROM USB!!! sorry about that outburst, its really annoying cos it boots on my laptop fine

---

