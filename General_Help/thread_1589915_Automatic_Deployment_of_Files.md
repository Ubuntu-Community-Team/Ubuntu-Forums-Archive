---
title: "Automatic Deployment of Files"
date: 2010-10-07
forum: General Help
---

### Post by cpressland on 2010-10-07
Hey Guys,

So I'm running a Call Center and the software we use runs on Java so I've decided to move the machines our agents sit on from a Windows XP base to a Ubuntu Base. I'll be modifying the system somewhat but theres a few things I need to bring over from Windows and need a little help with doing so, running without Active Directory will be the biggest issue but all things can be overcome.

Anyway, at current we have a Windows Batch file that sits in the users Startup folder and basically copies some files down from our server over Samba then runs the primary exe and closes itself, and it looks a little like this:

```
echo off
cls
echo Prepping Dialer Systems, Standby
C:
cd %appdata%
rmdir Contaque /S /Q
xcopy "\\192.168.19.21\Drobo\Contaque\Closer2H\*" "%appdata%\Contaque\Closer2H" /k /e /i
cd %appdata%\Contaque\Closer2H\
start Contaque.exe
exit

```

So for Ubuntu I plan to just have the folder in the Home Directory, I basically need something that'll delete ~/Contaque/ then connect to a Samba share to download files and place the files in ~/Contaque/ then create a launcher on ~/Desktop/ to launch a Java file inside the Contaque folder.

We do it this way because we frequently modify files for this application and we need to have the files deployed over all PCs every day so that they're running the latest version. Ideally this would be done at boot time before the user even logs in.

Any help with this would be great guys.
Thankyou so much, Ubuntu is about to gain an extra 300 PCs ;)

Chris Pressland

---

### Post by cpressland on 2010-10-07
Okay guys, so I'm doing this to download the files:

smbget -guest -R smb://192.168.19.21/Drobo/Contaque/*

now theres plenty of data inside the Contaque folder and it's just saying 0kb transfered. Any ideas?

---

### Post by cpressland on 2010-10-07
This done it..

```
rm -rf /home/contaque
mkdir /home/contaque
mkdir /home/contaque/Closer2H
cd /home/contaque/Closer2H
smbget -u root -p passwordhere -R -v smb://192.168.19.21/Drobo/Contaque/Closer2H
```

---

