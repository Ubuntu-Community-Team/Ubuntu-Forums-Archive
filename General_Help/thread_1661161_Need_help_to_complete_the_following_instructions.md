---
title: "Need help to complete the following instructions"
date: 2011-01-06
forum: General Help
---

### Post by moneyrules on 2011-01-06
Could someone tell me how to do this / The .bin file is located on my desktop sorry im a bigginer but I really need help with this . 

[LIST=1]
[*]Click this link to download the image: [[COLOR=#0000cc]https://dl.google.com/dl/chromeos/recovery/latest_mario_beta_channel[/COLOR]]("https://dl.google.com/dl/chromeos/recovery/latest_mario_beta_channel")
[*]Extract the .bin file from the .zip you just downloaded (e.g. [SIZE=3]ChromeOS--recovery.bin[/SIZE] ).
[*]Insert a USB Flash drive into your Linux computer's USB port.
[*]Open a terminal window and enter the following command: [SIZE=3]$ sudo fdisk -l[/SIZE] You should then see the drive name, such as [SIZE=3]/dev/sdc[/SIZE].
[/LIST][LIST=1]
[*]Enter and edit the following command: [SIZE=3]Run: $ sudo dd if=chromeos-recovery.bin of=/dev/sdX[/SIZE]
[*]Replace [SIZE=3]/dev/sdX[/SIZE] with the name of your USB device from step 4
[/LIST]
[LIST]
[*]Replace [SIZE=3]chromeos-recovery.bin[/SIZE] with the name of the file you extracted from step 2
[/LIST]

---

### Post by oldos2er on 2011-01-06
Which part are you having problems with?

---

### Post by moneyrules on 2011-01-06
I am having trouble telling terminal that my file is located on the desktop

---

### Post by oldos2er on 2011-01-06
The full path to a file *foo* on your desktop would be */home/user/Desktop/foo*

Hope that helps. If not, please post back.

---

