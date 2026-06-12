---
title: "Black screen after installation"
date: 2012-08-27
forum: General Help
---

### Post by Clucky on 2012-08-27
**LOOK AT POST BELOW FOR AN EDIT PLEASE**
I recently installed Ubuntu 12.04.1 LTS onto one of my two hard drives. I already have Ubuntu 11.04 on my first hard drive (the one inside the computer), however, due to recent issues, I have decided to just restart my whole hard drive (however I kept the old one in the computer to transfer files when I got the second one working). The second hard drive is in a hard drive enclosure connected to my computer using a USB cable.

The issue I am running into is that when I try to boot the second hard drive (the external one with Ubuntu 12.04) it goes to a flashing black screen with a white flashing underscore symbol. I tried accessing system recovery by holding left shift, did not work. I also tried pressing esc repetitively, that also failed.

The strange thing is, the internal hard drive containing Ubuntu 11.04 seems to work perfectly fine (other than the fact the graphics diver is corrupted along with several other servers, I have to start it in failsafe graphics mode from the recovery menu).

I did do a boot repair summary: [http://paste.ubuntu.com/1170552/](http://paste.ubuntu.com/1170552/)
I also did a boot repair: [http://paste.ubuntu.com/1170638/](http://paste.ubuntu.com/1170638/)
- - - - - - - - - - 

Processor: AMD Phenom II x4 840
Motherboard: Asus ... (I forget)

---

### Post by Clucky on 2012-08-27
...

---

### Post by jim_deadlock on 2012-08-28
This seems like a common problem with your graphics driver. If you can access GRUB, click 'e' to edit your boot options and add 'nomodeset' (without quotes) onto the end of the line starting with linux. That should enable you to boot into your desktop. Once you're in, run Additional Drivers (jockey), which may automatically pop up anyway, and install your nvidia driver or whatever it is you need. After that you should be able to boot normally without the GRUB edit.

---

