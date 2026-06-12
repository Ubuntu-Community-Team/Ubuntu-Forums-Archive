---
title: "Unable to mount location!?"
date: 2010-12-11
forum: General Help
---

### Post by Salama07 on 2010-12-11
Hello,
I am a Windows XP user. I recently received the "Blue Screen of Death - Unmountable_boot_volume" error while trying to start up my computer. I booted to Ubuntu 10.04 LTS from a LiveCD in an attempt to access all my important files and save them to a USB. I have not installed it fully for fear of losing all my data - I'm trying it without making any changes to my system. According to some instructions I found online, I need to go to Places and then Computer to access my files. This worked perfectly earlier in the summer when I encountered this BSOD problem; I was able to access my necessary files and save them to a USB (I've since lost said USB unfortunately = (

This time around when I went to Places and then computer the only folders that showed up are: "File System" and "100 GB Hard Disk: SQ004224P01". When I tried to open the latter it returned the following error: "DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken." Next, I tried to force Ubuntu to use that drive (even though there's something wrong with it) by typing in the following command in a new Terminal: mount -t vfat -o umask=1000 /dev/sda1 /media/disk. This did not work (I got some complicated error message).

As an Ubuntu novice, I have no idea what any of this means or how to proceed from here. All I know is that I absolutely, unequivocally need to recover my files. I'm a desperately poor college student who really cannot afford to pay to have my files recovered so any help you can provide would be very much appreciated! = )

---

