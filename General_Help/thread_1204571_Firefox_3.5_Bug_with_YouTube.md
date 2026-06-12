---
title: "Firefox 3.5 Bug with YouTube"
date: 2009-07-04
forum: General Help
---

### Post by Sukotto on 2009-07-04
I am using firefox 3.5 and when I am on youtube and click on the full screen button for any video I am watching. The browser crashes! every time.

---

### Post by Genius314 on 2009-07-04
Which flash plugin are you using? I've had mixed experiences with Firefox and Flash, although 3.5 hasn't had any problems for me (yet... :p)

---

### Post by PhilGil on 2009-07-05
I had the same problem; the solution is in this thread (response #14): [http://ubuntuforums.org/showthread.php?p=7487421](http://ubuntuforums.org/showthread.php?p=7487421) .  I added the line to the startup script (as described in the post) and all is well.

The biggest challenge for me was figuring out where to find the startup script on my machine (I used the ubuntuzilla install) - mine was at:* /opt/firefox/firefox* .

Cheers,
Phil

---

### Post by lovinglinux on 2009-07-05
> **PhilGil said:**
> I had the same problem; the solution is in this thread (response #14): [http://ubuntuforums.org/showthread.php?p=7487421](http://ubuntuforums.org/showthread.php?p=7487421) .  I added the line to the startup script (as described in the post) and all is well.

The biggest challenge for me was figuring out where to find the startup script on my machine (I used the ubuntuzilla install) - mine was at:* /opt/firefox/firefox* .

Cheers,
Phil

Yep. That fix worked for me too. In my case the file to edit was in /usr/local/lib/firefox-3.5/firefox. I have compiled Firefox 3.5, btw.

---

### Post by Sukotto on 2009-07-05
Cool Thanks!! I will do the fix when I get off work.

---

