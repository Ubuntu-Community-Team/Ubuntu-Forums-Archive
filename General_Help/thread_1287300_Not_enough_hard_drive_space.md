---
title: "Not enough hard drive space"
date: 2009-10-10
forum: General Help
---

### Post by bellboa45 on 2009-10-10
Hello. I am relatively new to Linux.I recently installed Ubuntu on to my sisters laptop for her. Before I reformated her windows laptop and installed ubuntu I backed up her 67 GB music folder onto an external usb hard drive. After the install was complete I tried to copy the music folder off of the external hdd onto the 80 GB hdd in the laptop but an error message came up saying that there was not enough disk space. When I fire up gparted the 80 GB reads as a 74.53 GB device and the /dev/sda1 partition I'm trying to copy onto reads as 73.11 GB with 69.86 GB free. Yet the error message I get while copying says that I require 67.2 GB and have 66.2 GB available. I dont"t understand why it won"t fit if I have 69 GB of free space. How did the folder fit on the bloated windows partion I took it off of? Please refer to the attached image if necessary. Thank you in advance for any help.

---

### Post by akakingess on 2009-10-10
I am not an expert in this area, but wanted to ask a question and shoot an idea out there. Is the partition formatted ext3 or ext4?  If so, I thought that I remember that the ext file system will "reserve" for lack of a better word about 10% of the drives space, so maybe that is the problem you are running into. Hopefully someone with a little more knowledge regarding this issue can chime in soon, but my initial thought was of the ext3/4 file system requirements.

---

### Post by bellboa45 on 2009-10-10
Thank you for your response. The filesystem is ext3.

---

### Post by akakingess on 2009-10-10
Alright, now if I were you I would start learning as much as I could about some of the quirks of an ext3 file system while waiting for someone that hopefully knows a lot more about that, but you may need to look into some alternatives as to what to do with the music files (new external drive, etc.) as that may be the best thing to do with so much data so that you don't end up completely filling a HD and risking it filling up at which point you can run into issues (drives in general no matter what OS or format don't like to get too full or they CAN start to have issues).

---

