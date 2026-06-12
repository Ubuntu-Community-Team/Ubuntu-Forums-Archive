---
title: "Cannot execute anything!?!?!"
date: 2010-04-30
forum: General Help
---

### Post by timinator94 on 2010-04-30
Hey all,
I have a serious problem...  i installed ubuntu 10.4 x86 and it wont let me execute anything to install... will post screens.. got the first one when i tried to change it to run as executable and the 2nd one is when i tried to run it in wine
Please help... i never had this problem in 9.10....
Thanks
The Timinator

---

### Post by mikewhatever on 2010-04-30
.exe`s are Windows executables, fairly useless when running Linux. I see you have the Software Center window open. That's the way to install software in Ubuntu.

---

### Post by linuxman94 on 2010-04-30
The reason it will not allow you to change the permissions is because it is a read-only file system (i.e. cdrom).  You chould be able to change the permissions if you copy all the files from the cd into a folder.

---

### Post by kill4killin on 2010-04-30
It looks like you may be trying to install Microsoft Office? Might I suggest using open office, it has the same capabilities...

If you're trying to run *.exe files, you will need to use wine so you're on the right track with that second screen shot. If you just try to run them you probably won't get anything useful except a can't run message.

Open up terminal and type in ```
cd /media/OFFICE12
``` and then type in ```
wine setup.exe
``` and then if that doesn't work try ```
sudo wine setup.exe
``` copy any errors it spits out from any of those attempts and we'll see what's going on from there.

---

### Post by ajgreeny on 2010-04-30
In the past, when I used wine, I could install programs from a CD by using terminal and giving the full pathway to the setup program, or by using cd to the correct CD folder containing the setup.exe file and simply running ```
wine setup.exe
```
I installed the whole of Lotus Smartsuite that way, needed at the time as OOo could not open .lwp files, which it can now.

---

### Post by kill4killin on 2010-04-30
> **linuxman94 said:**
> The reason it will not allow you to change the permissions is because it is a read-only file system (i.e. cdrom).  You chould be able to change the permissions if you copy all the files from the cd into a folder.

Interesting point, it might not be able to execute the setup.exe as it doesn't have the -x set on the file.

Try copying like he suggested and then run ```
sudo chmod 777 foldername
``` where "foldername" is whatever folder you copied your files to.

Then run the wine setup.exe and see if it works.

---

### Post by timinator94 on 2010-04-30
Ok thanks will try... i had wine installed and i use open office but i got my mom on ubuntu and she prefers ms office. so thanks for the replies and i will try it
edit- Got it thank you so much for the quick replies

---

