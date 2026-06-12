---
title: "Executing applications on external (USB) media"
date: 2011-11-08
forum: General Help
---

### Post by NekoMaster on 2011-11-08
For the past week since I installed Xubuntu 11.10 I've been trying to figure out how to run programs from my flash drives or USB hard drive. Since my drives are formated with NTFS I can't execute the file the usual way or enable it to run.

I've tried mounting my external media in fstab to let them execute files but then I run into another problem, if I remove my flash drive and plug it back it, it wont mount and gives me a error (something along the lines of "its already mounted")

Also, the execution script and mounting command on [http://askubuntu.com/questions/49392/how-to-mark-allow-executing-file-as-program-on-an-external-drive](http://askubuntu.com/questions/49392/how-to-mark-allow-executing-file-as-program-on-an-external-drive) don't work for me. The former complains about a missing file (not the executable but some lib file), while the other just doesnt work (remounting is currently unsupported).

Is there anyway to get NTFS external media to run applications will still being able to insert and remove it?

---

### Post by 3rdalbum on 2011-11-08
You haven't mentioned whether these programs are Windows or Linux. If they are Windows programs, then you need to run them with Wine directly. Go into the terminal and type 'wine ' and leave a space bar at the end, then drag the Windows program to the terminal. Click the terminal again to bring it to the front and then press Enter.

---

### Post by NekoMaster on 2011-11-08
Nothing executable works, linux app's, windows executables, and java jar's.

---

