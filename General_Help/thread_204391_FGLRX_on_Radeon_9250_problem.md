---
title: "FGLRX on Radeon 9250 problem"
date: 2006-06-26
forum: General Help
---

### Post by Shadix on 2006-06-26
As the title suggests I've been having troubles with FGLRX and Dapper.

I installed the driver using the methods provided by the wiki on it (method 1 AND method 2 in different installations), however, upon typing in the line 
"sudo aticonfig --overlay-type=Xv"
I was greeted with errors stating that nothing needed to be changed.  Upon rebooting my desktop looks like it is recieving over exposure, making certain colors more difficult to see (I think it's mainly orange).  I tried gamma correction via the ATI control panel and turned all the values down, and while I could see all the colors, it seemed murky with a lack of contrast.  Upon entering the "fglrxinfo" command into the terminal I was bombarded with errors.  (It also might be nice to note that my TV-Out does work, and the colors appear to be correct on the TV.)

---

### Post by twa1296 on 2006-06-27
I also have a Radeon 9250 and fglrx went haywire after an update. Fixed it using this thread: [http://ubuntuforums.org/showthread.php?t=185033&](http://ubuntuforums.org/showthread.php?t=185033&)

---

### Post by joshrobinson on 2006-06-27
[QUOTE=twa1296]I also have a Radeon 9250 and fglrx went haywire after an update. Fixed it using this thread: [http://ubuntuforums.org/showthread.php?t=185033&](http://ubuntuforums.org/showthread.php?t=185033&)[/QUOTE]

if its the same error as the one in the thread twa1296 posted, fix it that way.. im the one who hosted the file that everyone is using.. so i was gona tell you to do exactally what twa1296 linked :p

---

### Post by Shadix on 2006-06-27
Thank you a bunch.  It's working perfectly now.


My next question though is how do you enable hardware acceleration :E.

---

