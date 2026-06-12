---
title: "Problem &quot;Permisson Denied, please see the log file [Archive]&quot;"
date: 2011-12-31
forum: General Help
---

### Post by MxRxV on 2011-12-31
While i try to install Wubi on my computer, when the installation finishes, appears this:

Also check the text file of the error, PLEASE HELP ME !!

[http://www.megaupload.com/?d=E3IIUD2F]("http://www.megaupload.com/?d=E3IIUD2F")

[IMG]http://a2.sphotos.ak.fbcdn.net/hphotos-ak-ash4/403958_348638911819289_100000195481874_1547718_1369552525_n.jpg[/IMG]

---

### Post by MG&amp;TL on 2011-12-31
Obvious question, but need to remove doubt first-are you the administrator user on that computer?

---

### Post by MxRxV on 2011-12-31
> **MG&TL said:**
> Obvious question, but need to remove doubt first-are you the administrator user on that computer?

[COLOR="Red"]YES I AM THE ADMINISTRATOR. Please I need help.[/COLOR]

---

### Post by Karlchen on 2011-12-31
Hello, MxRxV.

Wubi should create the files C:\Wubildr and C:\Wubildr.cfg, because as far as I can tell from the Wubi installation logfile wubi-11.10-rev245.log, you are running a Windows XP system and XP boots from drive C:. Correct?
Yet, in the Wubi installation logfile wubi-11.10-rev245.log, there are two places where the Wubi installer complains that it has not got the permission to create the file H:\wubildr. (On set of error message for each installation attempt) H: seems to be a removable USB drive. Wubi should not even be trying to create H:\wubildr.
> 12-30 13:54 ERROR  TaskList: [Errno 13] Permission denied: 'H:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'H:\\wubildr'
12-30 13:54 DEBUG  TaskList: # Cancelling tasklist
12-30 13:54 DEBUG  TaskList: # Finished tasklist
12-30 13:54 ERROR  root: [Errno 13] Permission denied: 'H:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'H:\\wubildr'> 2-31 13:27 ERROR  TaskList: [Errno 13] Permission denied: 'H:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'H:\\wubildr'
12-31 13:27 DEBUG  TaskList: # Cancelling tasklist
12-31 13:27 DEBUG  TaskList: # Finished tasklist
12-31 13:27 ERROR  root: [Errno 13] Permission denied: 'H:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'H:\\wubildr'Personally I would proceed like this:
[LIST]
[*]remove the failed Wubi installation
[*]copy the Ubuntu ISO file plus wubi.exe to the same folder on drive C:
[*]remove any removable drives, i.e. remove any DVDs and detach any USB sticks or drives
[*]relaunch the Wubi installation and tell it to install Ubuntu to drive D: as you have done
[/LIST]
One question which may or may not be relevant to the problem: you are trying to install a 64-bit Oneiric Ocelot version. You are certain that your machine can run 64-bit software, because you have tested the Oneiric 64-bit live system?!

You are sure you are using exactly the WUBI.EXE that comes with the Ubuntu ISO image which you are trying to install? Different wubi.exe versions are not compatible with each other. If need be extract the wubi.exe from the root folder of the ISO file with the help of 7zip.

Kind regards,
Karl

---

### Post by MxRxV on 2012-01-01
> **Karlchen said:**
> Hello, MxRxV.

Wubi should create the files C:\Wubildr and C:\Wubildr.cfg, because as far as I can tell from the Wubi installation logfile wubi-11.10-rev245.log, you are running a Windows XP system and XP boots from drive C:. Correct?
Yet, in the Wubi installation logfile wubi-11.10-rev245.log, there are two places where the Wubi installer complains that it has not got the permission to create the file H:\wubildr. (On set of error message for each installation attempt) H: seems to be a removable USB drive. Wubi should not even be trying to create H:\wubildr.
Personally I would proceed like this:
[LIST]
[*]remove the failed Wubi installation
[*]copy the Ubuntu ISO file plus wubi.exe to the same folder on drive C:
[*]remove any removable drives, i.e. remove any DVDs and detach any USB sticks or drives
[*]relaunch the Wubi installation and tell it to install Ubuntu to drive D: as you have done
[/LIST]
One question which may or may not be relevant to the problem: you are trying to install a 64-bit Oneiric Ocelot version. You are certain that your machine can run 64-bit software, because you have tested the Oneiric 64-bit live system?!

You are sure you are using exactly the WUBI.EXE that comes with the Ubuntu ISO image which you are trying to install? Different wubi.exe versions are not compatible with each other. If need be extract the wubi.exe from the root folder of the ISO file with the help of 7zip.

Kind regards,
Karl

I just noticed that my comp is 32-bit, thank you, but. Wubi still being an option or it can't install on a 32-bit comp?. I'm just a beginner, and i want to learn linux, sooo, do you think there is another version of linux that maybe works on 32 bit?

---

### Post by MG&amp;TL on 2012-01-02
[https://wiki.ubuntu.com/WubiGuide]("https://wiki.ubuntu.com/WubiGuide")

Either download the 32-bit ISO, or start wubi like this:


```
cd C:/path/to/where/you/downloaded/wubi
wubi.exe --32bit
```

---

### Post by bcbc on 2012-01-02
See bug [lpbug]862003[/lpbug] for the original prob. 

Regarding the 64bit issue. Wubi doesn't get 32bit vs 64bit wrong. You might have a 32bit windows OS but that doesn't matter.

---

