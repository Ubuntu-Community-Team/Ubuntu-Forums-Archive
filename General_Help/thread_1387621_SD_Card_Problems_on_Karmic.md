---
title: "SD Card Problems on Karmic"
date: 2010-01-22
forum: General Help
---

### Post by Lavahead on 2010-01-22
I am attempting to copy files to a 1GB SD card using my built-in SD card reader on my notebook computer. Mind you, this function worked great on Hardy Heron. However, I switched to Karmic Koala about a week ago.

Upon insertion of the SD card, the entire desktop (including mouse cursor) will freeze for about 30 seconds. Then, the SD card apparently mounts with an icon showing on the desktop. I can then open Nautilus and view the files and folders on the card.

When I attempt to copy a file over to the SD card, the transaction looks as though it completes because the file icon shows up. However, Nautilus suddenly unmounts the card. When I check the file, I find that only half or less has copied over the the SD card. Any suggestions?

---

### Post by prshah on 2010-01-22
> **Lavahead said:**
> 
Upon insertion of the SD card, the entire desktop freeze for about 30 seconds. 

Nautilus suddenly unmounts the card. 

If you have had several abrupt unmounts, your card may need a filesystem check.

Plug the card in, then unmount it. Check in the dmesg ( dmesg | tail ) for the device ID eg, /dev/sdf1.

Run an fsck on it```
sudo fsck -r /dev/sdf1
``` If you would prefer an automatic repair (may lose some files, data, doesn't work always) you can use "-a" instead of "-r"

You may have to run it twice or more until you get no errors at all.

A backup of the current contents before you start is a good idea.

---

### Post by Lavahead on 2010-01-23
Thank you for the timely response.

I attempted to copy the file again this evening. This time, the SD card mounted quickly without freezing the desktop. I had to try three times to copy the file, although the SD card did not unmount itself. Finally, the file copied over. The entire desktop became jerky including the mouse cursor. I then unmounted the card. No change in the jerky behavior. Eventually, I had to restart the computer.

I will run fsck on the SD card later this evening. However, I suspect that something else is causing the problem, although I have no idea what it is. Any ideas?

---

### Post by Lavahead on 2010-02-06
The SD card file system was fine. What the problem seems to have been is that Gnome/Nautilus attempts to open a specific application (i.e., F-Spot) when the SD card is inserted into the reader since photo files are most commonly stored on SD cards.

I had already uninstalled F-Spot, and I only use the SD card to store audio files. After unchecking the box for "Never prompt or start programs on media insertion" in Nautilus Preferences, fileoperations work fine again.

---

