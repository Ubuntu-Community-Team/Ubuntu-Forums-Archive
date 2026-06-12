---
title: "How do I install wine and steam on ubuntu?"
date: 2011-07-26
forum: General Help
---

### Post by Dark Dane on 2011-07-26
I have never used ubuntu or any other linux operating system, I normally use windows 7, however, lately my laptop has been having a lot of issues and eventually reached a point where it wouldn't even start up. I attempted to format my hard drive and reinstall windows 7 but the installation always failed, so I tried ubuntu and was able to get it installed successfully. I play a ton of games and have well over 100 on steam, and from what I've heard steam can be installed on ubuntu if wine is used. 

So, I'd like to install wine and steam but I have absolutely no idea how to do it.  I've been looking through a variety of guides on how to install wine and steam but all the guides I looked at are either fairly outdated, or they explain what to do but not how to do it. I have never used ubuntu or any other linux operating system so when guides explain doing things that are specific to these operating systems it makes no sense to me. The guides also often tell me to search for something in the software center or somewhere else and download it, but there's always more than one choice, how am I supposed to know which is the right one if none of them match the name for the thing I'm supposed to download?  

For example, I followed this guide: [https://wiki.ubuntu.com/UbuntuMagazine/HowTo/InstallingSteam](https://wiki.ubuntu.com/UbuntuMagazine/HowTo/InstallingSteam). I did the first step and installed wine the way it said to, I then downloaded steam. It then says to run wine iexplore and install gecko but it doesn't tell me how. It provides a link to winehq.org, but going there I see nothing about iexplore or gecko. So, I just skipped that step and went to the next one. I don't have windows installed so I downloaded that tahoma.tff font from the internet, but I have no idea how to copy it to that directory. I tried searching my file system for the folder to copy it to, but when I searched for it I couldn't find it, so I skipped that step as well. I typed in msiexec /i SteamInstall.msi, but it didn't do anything for some reason, so, instead I did what another guide showed and went into properties, then permissions, and checked the run as executable box and then installed it. I had no trouble installing it, but I can't get it to work. When I try to run it, it starts up but after a few seconds it just closes and I don't know why.  Can someone please help me out? I have no idea what to do and none of these guides are helping because they all assume I know how to use ubuntu but I don't. I would really appreciate it if someone could provide me with some clear step by step instructions for how to successfully go about installing wine and steam.

---

### Post by lkjoel on 2011-07-26
Open up a Terminal window, and type in it:
```
sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update
sudo apt-get install wine1.3
```
Then try to install steam

---

### Post by Dark Dane on 2011-07-26
That is the same way that I installed wine. I initially misread the guide I linked and thought it said type in sudo apt-get to install wine instead of type in sudo apt-get install wine so I couldn't get it working because I was leaving out the install wine part. Another guide I looked at told me to type in those same 3 lines you provided though and that's how I installed wine. I typed it all in again to be sure though and it said:
"Reading package lists... Done
Building dependency tree       
Reading state information... Done
wine1.3 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 188 not upgraded."

---

### Post by lkjoel on 2011-07-26
> **Dark Dane said:**
> That is the same way that I installed wine. I initially misread the guide I linked and thought it said type in sudo apt-get to install wine instead of type in sudo apt-get install wine so I couldn't get it working because I was leaving out the install wine part. Another guide I looked at told me to type in those same 3 lines you provided though and that's how I installed wine. I typed it all in again to be sure though and it said:
"Reading package lists... Done
Building dependency tree       
Reading state information... Done
wine1.3 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 188 not upgraded."
It might help if you do a system update.
```
sudo apt-get dist-upgrade
```

---

### Post by Dark Dane on 2011-07-26
Alright, I typed that in and it's done updating, what should I do now?

---

### Post by lkjoel on 2011-07-26
> **Dark Dane said:**
> Alright, I typed that in and it's done updating, what should I do now?
Restart, and try steam again.

---

### Post by Dark Dane on 2011-07-26
I restarted my computer but steam still isn't working. It seems to work at first, the wine icon appears on the sidebar and something saying connecting steam account pops up like usual, however, it eventually closes and the icon disappears from the sidebar. Every few times I have tried steam has opened, but then after a second or two that too just disappears.

---

### Post by lkjoel on 2011-07-26
Try this: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=19444](http://appdb.winehq.org/objectManager.php?sClass=version&iId=19444)

---

### Post by Dark Dane on 2011-07-26
Thanks so much for the help, that worked. For some reason the first thing it said to type in didn't work the first time I tried it, but when I tried it again it downloaded fine. Now that I have steam running properly do you think most of the games will work on ubuntu? If not it doesn't really matter too much because I still have my other computer, I just hope at least a few games like team fortress 2 will work fine.

---

### Post by lkjoel on 2011-07-26
To find if your games will work with WINE: [http://appdb.winehq.org/index.php](http://appdb.winehq.org/index.php)

---

### Post by Dark Dane on 2011-07-26
Oh nice, thanks, it looks like most if not all of the games I'm planning on installing should work fine with ubuntu, whether my laptop can run them is another question though. Thanks for all of the help, I really appreciate it.

---

