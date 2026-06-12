---
title: "Connecting Samsung Galaxy tab 10.1."
date: 2011-12-24
forum: General Help
---

### Post by Sinopa on 2011-12-24
Yesterday I bought a Samsung Galaxy tab 10.1 (P7500) and I can't mount the storagespace on it. I installed MTP, but still nothing. Can anyone out there please help me solve this? :)

Merry Christmas All :)

---

### Post by hansdown on 2011-12-24
Hi, Sinopa.

All I could find, was this...

[http://www.addictivetips.com/mobile/use-samsung-galaxy-tab-10-1-as-mass-storage-device-guide/](http://www.addictivetips.com/mobile/use-samsung-galaxy-tab-10-1-as-mass-storage-device-guide/)

---

### Post by r_avital on 2012-03-17
Here's some more info:

[http://lifeafter2am.net/2011/07/connecting-samsung-galaxy-tab-10-1-to-linux/](http://lifeafter2am.net/2011/07/connecting-samsung-galaxy-tab-10-1-to-linux/)

[http://forum.xda-developers.com/showthread.php?t=1077377](http://forum.xda-developers.com/showthread.php?t=1077377)

Be very, very careful with the second one.  It's pretty detailed, and involved editing fstab, and the slightest mistake might make your system unusable (unable to mount any drives).

I haven't yet fully experimented with it.

---

### Post by timjohn7 on 2012-09-27
I have the same issue with the Galaxy Note 10.1 running Ice Cream Sandwich. Great tablet, but not a case of "it just works...". I'm still looking for a simple solution.

---

### Post by timjohn7 on 2012-09-27
I have found a solution for the Galaxy Note 10.1.  I'm not sure whether it will work for your Tab, but give it a try. It is simple but not entirely clear; it works.

1.  Install gMTP
```
sudo apt-get install gmtp
```

2.  Connect your tablet using the supplied proprietary cable to a free USB port.

3.  I got the "Could not connect" message as before. I could not connect using gMTP either.

4. Open the Notification area on your tablet and select the USB Notice.  Mine says "Connected as a camera".  Select this and you should be in the Settings Menu "Storage Settings > USB PC connection" (NOT visible from the normal Settings Menu in my case).

5.  There are 2 selections, either Media Device (MTP) or Camera (PTP).  When I select Media Device, I can access all the Tablet Files on my PC using gMTP normally.

---

### Post by DirkIT on 2012-10-18
I can confirm that gMTP also works for my Galaxy Tab 10.1 :)

I launch gMTP, then connect the cable, then hit the connect button... 

It takes a quite a few seconds before the file list appears though - looks like it reads the tree etc.

---

