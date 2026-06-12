---
title: "Problems with youtube..."
date: 2009-06-28
forum: General Help
---

### Post by CharlesWelsh on 2009-06-28
I have downloaded and installed the latest flash player.... And i have ran the update manager. The videos in you tube give me sound and the video playback is horrible... This is my first day using Ubuntu (9.0.4) So please... spare me the criticism... Thanks in advance -CJ

---

### Post by QIII on 2009-06-28
No criticism for being new.   We were all once!  Welcome.

If you "downloaded" through Synaptic, you may have the sorts of problems you are describing.

You need to go to Adobe's website ([www.adobe.com]("http://www.adobe.com")) and download the 64 bit libflashplayer.so or 32 bit libflashplayer.so, depending on your Ubuntu install.  Just click the "Get Adobe Flash Player" button.   Under "Select Version to Download", choose the .tar.gz file. When you download the appropriate one, the default archive manager will ask if you want to extract them.

Extract them to your whateveryournameis directory.  Shut down your browser.

Open the terminal ( Applications | Accessories | Terminal) and type


cp libflashplayer.so ~/.mozilla/plugins

---

### Post by lovinglinux on 2009-06-28
[Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567)

---

