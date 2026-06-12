---
title: "New to Ubuntu - Questions."
date: 2010-06-17
forum: General Help
---

### Post by whitefish10 on 2010-06-17
Hi guys, I am thinking of installing the new Ubuntu 10.04 64bit. It had been a while since I used Linux, There are somethings the I need to clear before doing anything:-


[LIST=1]
[*]I currently having three partitions, (Windows, data, data). If I installed Ubuntu on the windows partition. Can I access the other two partitions (they are NTFS)? I need a full read and write support coz most of the time I download some stuff directly on the data partition (like torrent).
[*]I download flash videos from the web (.flv). I need a software to do so and something to converted to other formats like (.mp4).
[*]I have an Iphone 3gs and I usually send .mp3 and .mp4 to it using Itunes in windows. I need something similar in Ubuntu.
[/LIST]

Note: For NO.1,  I need a step by step instructions of how to mount the two data partitions and put the icons on the desktop.

thanks in advance.

---

### Post by Smart Viking on 2010-06-17
1. Yes you can.

2. I think it is pretty easy to do from the command line, but i have never needed to do so, so i don't know.

3. no idea

Hope this helped a little, but in n.1, it will not always mount automatically, if it wont then you would only have to learn a little about the "mount" command, which is not that hard. :)

---

### Post by bruno9779 on 2010-06-17
1. Accessing your data partitions is pretty straight forward.
Even on the live CD you can see that working: boot the live CD to desktop, then right click the top panel and click "add".
Choose "disk mounter" from the gui.

Now you should see an icon on the top bar for any of your data partitions.

UIf you later wan't them to mount automatically, you will need to edit fstab

2. When it comes to flash, the are many approaches. The one that works best for me is Firefox addon "Videodownloadhelper".
It can be easily configured to encode .flv into anything else supported by ffmpeg.

3. I don't have experience with I-pods, but I have seen many threads about it on this forum

---

### Post by pmlxuser on 2010-06-17
for ipod i know rythmbox to do the trick else you can use banshee

---

