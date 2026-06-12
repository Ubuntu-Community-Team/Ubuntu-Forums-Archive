---
title: "The Case of the Missing Files"
date: 2011-05-14
forum: General Help
---

### Post by bdacanay on 2011-05-14
Hello all, I am a fairly new user to Ubuntu, so please excuse me if I sound a bit noobish. So here's the back story. I recently installed Ubuntu after my Windows XP OS recently crashed on me. I plan on fixing it, so I installed Ubuntu 10.04 Netbook Remix alongside XP. I haven't had any problems with it until today and I cannot figure out a cause of what happened.

This morning I was able to navigate to my My Documents folder on my HD from XP. Inside of that folder is my Downloads folder. Whenever I opened that folder earlier, I could see all of my documents and such, but currently I cannot see anything in the folder. The space left on the disk has not changed at all, so I know they're still there...but they're not.

I have not installed any system files since then. Only Chrome and Vuze. I have not even shut down my computer since yesterday. I have searched for specific files in the Downloads folder, but the search returns nothing. I have also made sure that they are not in the Trash Bin.

Thanks for your patience, and hopefully a prompt response.

---

### Post by dragonfly41 on 2011-05-14
Before going any further .. in Win XP .. have you tried searching for specific file(s) in the entire c:\ directory (not just Downloads) .. adding any filters (date and/or extension in search expression) to speed up the process?

I don't understand why your documents are in Downloads?

---

### Post by mikewhatever on 2011-05-14
These are. quite probably, file system problems on the Windows partition. You may be able to fix them by running chkdsk in Windows. For more info, check out the MS support page: [http://support.microsoft.com/kb/315265](http://support.microsoft.com/kb/315265).

---

### Post by bdacanay on 2011-05-14
I can't get onto XP at all. It's pretty much corrupt. I just don't see how the files could have disappeared when I haven't even touched Windows in two weeks.

---

### Post by dragonfly41 on 2011-05-14
> I can't get onto XP at allLet's start with the basics ..

Q1.   Exactly what symptoms do you see in trying to boot into XP?  Blue screen?

Q2.   Can you get into XP in safe mode?  F8.

Q3.   Do you have an XP installation disc to try REPAIR (not reinstallation) of XP?

Q4.   Can you get into ubuntu and run sudo fdisk -l in terminal to view your partitions?

more to follow ...

[EDIT]

See also this related thread ..

[http://ubuntuforums.org/showthread.php?t=1757089](http://ubuntuforums.org/showthread.php?t=1757089)

---

### Post by bdacanay on 2011-05-14
Thanks for the help, but I got the files to show after running chkdsk.

---

