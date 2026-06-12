---
title: "firefox gone mad!!!"
date: 2009-07-14
forum: General Help
---

### Post by rudi009 on 2009-07-14
well this is the most strange problem i've ever had...yesterday when i fired up firefox what i found was that all my history and bookmarks are gone.](*,)..and if thats not enough i'm now not even able to make new bookmarks and the four common buttons on the navigation toolbar (back, forwrd, stop ,refresh)have faded and not working..help!! i want to know what happened and does anybody has any similar experience???

---

### Post by andrewc6l on 2009-07-14
Is there a chance you've run firefox as root (sudo firefox)? That might have changed ownership of files from you to root.

You could check this by looking at where firefox stores its config files - ~/.mozilla/firefox or ~/.firefox, I'd guess - and seeing who owns the files. If it's not you, it should be :-)

---

### Post by lovinglinux on 2009-07-14
See **Solution** [*[COLOR="Red"]**FOT003**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT003).

---

