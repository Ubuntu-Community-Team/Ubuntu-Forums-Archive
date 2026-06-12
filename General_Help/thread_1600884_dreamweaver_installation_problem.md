---
title: "dreamweaver installation problem"
date: 2010-10-19
forum: General Help
---

### Post by suresh_vandiyur on 2010-10-19
now  we  begin to  copy  folder from windows  to  ubuntu .

2-navigate to C:\Program Files. Copy the whole ‘Adobe‘ folder to Ubuntu /home/username/.wine/drive_c/Program Files folder.

3- **copy  C:\Documents and Settings\your-windows-user-name\Application Data  to /home/username/.wine/drive_c/windows/profiles/All Users/Application Data/**

4-copy C:\Program Files\Common Files  to /home/username/.wine/drive_c/Program Files/Common Files

5- copy  C:\WINDOWS\system32  to /home/username/.wine/drive_c/windows/system32

6-copy   Winsxs  from   C:\windows    to /home/username/.wine/drive_c/windows/  (this folder is  verry  important)

7-  import   the  registery to  wine 


my doubt is the where is the /home/username/.wine/drive_c/windows/profiles/All Users/Application Data/. please tell where i can application data files in ubunt 10.04 LTS

Thank you

---

### Post by ivarn on 2010-10-19
I thought this was about dreamweaver, so what the hell are you trying to do here?
Wine is just a windows emulator. made to run SOME windows apps on linux.
All you need to copy from c: is the program files/dreamweaber folder.
Also, why don't you just mount the windows partition in ubuntu so u don't have to move or copy anything? Just go to your program files folder, find dreamweaver and open up dreamweaver.exe with Wine.

---

### Post by suresh_vandiyur on 2010-10-19
> **ivarn said:**
> I thought this was about dreamweaver, so what the hell are you trying to do here?
Wine is just a windows emulator. made to run SOME windows apps on linux.
All you need to copy from c: is the program files/dreamweaber folder.
Also, why don't you just mount the windows partition in ubuntu so u don't have to move or copy anything? Just go to your program files folder, find dreamweaver and open up dreamweaver.exe with Wine.
please see this [http://www.unixmen.com/linux-tutorials/324-install-dreamweaver-cs4-in-ubuntudebian](http://www.unixmen.com/linux-tutorials/324-install-dreamweaver-cs4-in-ubuntudebian). am trying to install Dream weaver cs4 in ubuntu10.04. if you know about the dream weaver installation means reply 

Thank you

---

### Post by ivarn on 2010-10-19
OK, delete everything you have copied from the windows folder and all that crap, remove the wine package and go to winehq.org and install the newest version from there.
The wine version in synaptic doesn't support the CS4 programs since the wine version is older.
If you want to have the dreamweaver software on your ubuntu partition, copy the Dreamweaver folder ONLY or you can run the dreamweaver setup.
Just so you know, dreamweaver cs4 is not yet 100 % stable with Wine so if you use it often, I would go for dreamweaver MX 2004 or dreamweaver 8 instead since they are.
If you wonder what windows programs you can run with wine, check out the same webpage ([www.winehq.org](www.winehq.org)).
Good luck.

---

### Post by suresh_vandiyur on 2010-10-19
> **ivarn said:**
> OK, delete everything you have copied from the windows folder and all that crap, remove the wine package and go to winehq.org and install the newest version from there.
The wine version in synaptic doesn't support the CS4 programs since the wine version is older.
If you want to have the dreamweaver software on your ubuntu partition, copy the Dreamweaver folder ONLY or you can run the dreamweaver setup.
Just so you know, dreamweaver cs4 is not yet 100 % stable with Wine so if you use it often, I would go for dreamweaver MX 2004 or dreamweaver 8 instead since they are.
If you wonder what windows programs you can run with wine, check out the same webpage ([www.winehq.org](www.winehq.org)).
Good luck.

just now i have installed wine. please remove same or not

---

### Post by suresh_vandiyur on 2010-10-19
> **suresh_vandiyur said:**
> just now i have installed wine. please remove same or notwine: cannot find L"C:\\windows\\system32\\install.exe"
i try install dreamweaver i get the above error.

thank you

---

### Post by suresh_vandiyur on 2010-10-19
> **suresh_vandiyur said:**
> wine: cannot find L"C:\\windows\\system32\\install.exe"
i try install dreamweaver i get the above error.

thank you-desktop:~/Adobe Dreamweaver CS3$ wine Dreamweaver.exe

i have attached the error mes while installain the dreamweaver

---

