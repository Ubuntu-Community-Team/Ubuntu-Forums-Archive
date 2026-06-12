---
title: "Infect unmounted partition?"
date: 2006-06-15
forum: General Help
---

### Post by squeky on 2006-06-15
Just curious, can an unmounted Windows partition be infected through a Windows virus?  I've been contemplating installing AVG or something similar, but don't have any mounted Windows partitions (they are all unmounted).  Thanks.

---

### Post by RAOF on 2006-06-15
No, and it wouldn't be even if it were mounted.  Windows viruses only do anything when you're running in windows.

Of course, you could still download a virus attachment to the windows partition, then boot up Windows and run it there.  But you'd need to manually run it, and any competant anti-virus should catch it before you do.

---

### Post by yager on 2006-06-15
That would be quite a feat for the virus given it would have to figure out how to execute inside Ubuntu first.  Then it would have to figure out how to get you to run it since you would have to allow it to have root privileges so it could mount the drive.  Then finally it would have to figure out if you had something like NTFSfuse installed so it could actually move the infection on to the Windows partition.  Lastly, you would then have to switch back to Windows to actually experience the infection.

The kid who puts this one out will end up working for the NSA getting you to give all of your private information to his super computer.  Fear HIM!!!

Not likely.  There are easier ways that don't involve Linux.  Its called Windows.

---

### Post by squeky on 2006-06-15
So why do people recommend anti-virus for dual boots?  Copying an infected file over to a Windows part to be executed later or passing it along to friends?  I haven't had a Windows virus in about 8-9 years, I'm not really concerned with them in Windows either to be honest.

---

### Post by yager on 2006-06-15
Its for your friends who are still using Windows.  While you do not become infected, you can act as a carrier.  This of course is based on the premise that the virus is travelling through your system as an email or perhaps a download of an infected file.  You will not have a problem but they will unless they have AV active on their system.

---

