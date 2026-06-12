---
title: "pen drive doesnot permit to cut-paste"
date: 2010-08-17
forum: General Help
---

### Post by amite on 2010-08-17
i gave my pen drive to my friend who is using window system.and now when i tried to delete two files autorun.inf and Rahul'sVirusprotection.vbe it give error message Error removing file: Read-only file system.
here is the content of RhulVirusprotection.vbe
> 
[autorun]
open=wscript.exe Rahul'sVirusprotection.vbe
icon=%systemroot%\System32\SHELL32.dll,8
action=Open folder to view files
shell\open=Open
shell\open\Command=wscript.exe Rahul'sVirusprotection.vbe
shell\Auto=AutoPlay
shell\Auto\Command=wscript.exe Rahul'sVirusprotection.vbe
shell\Explore\Command=wscript.exe Rahul'sVirusprotection.vbe
shell\Find=Search...
shell\Find\Command=wscript.exe Rahul'sVirusprotection.vbe
shell\Format...=Format...
shell\Format...\Command=wscript.exe Rahul'sVirusprotection.vbe



$ ls -al /media/
drwx------  2 amitesh amitesh 4096 1970-01-01 05:30 2C82-97EF

$ls -al /media/2C82-97EF/
-r-xr-xr-x 1 amitesh amitesh   1046 2007-01-01 00:10 autorun.inf
-rwxr-xr-x 1 amitesh amitesh 635247 2010-05-24 16:11 Image2461.jpg
-r-xr-xr-x 1 amitesh amitesh  19220 2007-01-01 00:10 Rahul'sVirusprotection.vbe

$ chmod g+w /media/2C82-97EF/
chmod: changing permissions of `/media/2C82-97EF/': Read-only file system
$ ls -al /media/
drwx------  2 amitesh amitesh 4096 1970-01-01 05:30 2C82-97EF
~$ rm -f /media/2C82-97EF/autorun.inf 
rm: cannot remove `/media/2C82-97EF/autorun.inf': Read-only file system


while last time i used my pen drive on my system it was doing fine.Can any one suggest me what is going wrong and how any window's script can affect linux system(if my prob is due to that script)

---

### Post by Yogotiss on 2010-08-17
> **amite said:**
> i gave my pen drive to my friend who is using window system.and now when i tried to delete two files autorun.inf and Rahul'sVirusprotection.vbe it give error message Error removing file: Read-only file system.
here is the content of RhulVirusprotection.vbe


$ ls -al /media/
drwx------  2 amitesh amitesh 4096 1970-01-01 05:30 2C82-97EF

$ls -al /media/2C82-97EF/
-r-xr-xr-x 1 amitesh amitesh   1046 2007-01-01 00:10 autorun.inf
-rwxr-xr-x 1 amitesh amitesh 635247 2010-05-24 16:11 Image2461.jpg
-r-xr-xr-x 1 amitesh amitesh  19220 2007-01-01 00:10 Rahul'sVirusprotection.vbe

$ chmod g+w /media/2C82-97EF/
chmod: changing permissions of `/media/2C82-97EF/': Read-only file system
$ ls -al /media/
drwx------  2 amitesh amitesh 4096 1970-01-01 05:30 2C82-97EF
~$ rm -f /media/2C82-97EF/autorun.inf 
rm: cannot remove `/media/2C82-97EF/autorun.inf': Read-only file system


while last time i used my pen drive on my system it was doing fine.Can any one suggest me what is going wrong and how any window's script can affect linux system(if my prob is due to that script)



What happens if you open and try to delete as root? You can also try to copy everything you want to a folder your desktop if you can. Then use GParted to format the drive or use Windows to format the drive.

---

### Post by amite on 2010-08-17
> What happens if you open and try to delete as root? You can also try to copy everything you want to a folder your desktop if you can. Then use GParted to format the drive or use Windows to format the drive.

i didn't try with super user account but i tried with sudo command and the result was same.
also i want to know why the permission is not changing when i m using chmod

---

