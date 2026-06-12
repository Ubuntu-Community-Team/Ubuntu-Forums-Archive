---
title: "Connecting MP3 player"
date: 2009-07-14
forum: General Help
---

### Post by brasada on 2009-07-14
I have connected a Sansa Clip Mp3 player via a USB port to my notebook. Ubuntu finds the Sansa just fine. In fact, an Sansa Clip icon appears on my desktop and asks if I want to open the files on the device.

The problem is that when I open the folders where I have music, or in my case audio books, it says all the folders are empty. 

I know this is not true. Why can't Ubuntu see any of the music or books on my player?

Thanks, 

Byron.

---

### Post by ManiacDan on 2009-07-14
Ubuntu by default hides a number of files.  Maybe they start with a period, or they were set to "hidden" in Windows (unlikely this will affect Ubuntu's problem).  Open the command line and navigate to the mount for that device (normally it's under /media/) and do an ls -al.  That should show your files, and you can see what may be hiding them.

-Dan

---

