---
title: "Beginners problems"
date: 2011-12-03
forum: General Help
---

### Post by UbuBegUsr on 2011-12-03
Hello, it's the first time in Ubuntu. I faced many problems. RAM: 1 GB, VGA: _Nvidia 7300 GS_.
   1. In Additional Drivers, I installed version: Current (Recommended) but everything froze and I had to reinstall Ubuntu. I installed version: 173 but I couldn't change the resolution and I had to remove it. What version should I install?
   2. I don't know where's the audio drive version for Linux to download.
   3. I installed Game: Savage 2 by following this steps:
```
mkdir ~/.Games
cd ~/Desktop
chmod +x Savage2Install-1.5.0-x86_32.bin
./Savage2Install-1.5.0-x86_32.bin
```
   Can someone explain this way to me?
   4. After installing the game, I didn't find where's it to play it (_My Ubuntu version: 11.10_). I couldn't find ".Games" file.
   4. I downloaded Adobe Flash from its website and I download a file its extension is .tar.gz How to install it (_Using this file_)?

---

### Post by oldtimer7777 on 2011-12-03
It might be helpful to use a walkthrough if you are new to installing Ubuntu 11.10:

[https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

> **UbuBegUsr said:**
> Hello, it's the first time in Ubuntu. I faced many problems. RAM: 1 GB, VGA: _Nvidia 7300 GS_.
   1. In Additional Drivers, I installed version: Current (Recommended) but everything froze and I had to reinstall Ubuntu. I installed version: 173 but I couldn't change the resolution and I had to remove it. What version should I install?
   2. I don't know where's the audio drive version for Linux to download.
   3. I installed Game: Savage 2 by following this steps:
```
mkdir ~/.Games
cd ~/Desktop
chmod +x Savage2Install-1.5.0-x86_32.bin
./Savage2Install-1.5.0-x86_32.bin
```   Can someone explain this way to me?
   4. After installing the game, I didn't find where's it to play it (_My Ubuntu version: 11.10_). I couldn't find ".Games" file.
   4. I downloaded Adobe Flash from its website and I download a file its extension is .tar.gz How to install it (_Using this file_)?

---

### Post by grahammechanical on 2011-12-03
You should not need an audio driver for Linux. These are built in. You may need to unmute the audio. Click on the sound icon and tick Unmute. From that menu you can open Sound Settings where you can set the audio device and the input and output devices. You may find that these are also muted. So, look for that as well.

Regards.

---

### Post by carranty on 2011-12-03
> **UbuBegUsr said:**
> Hello, it's the first time in Ubuntu. I faced many problems. RAM: 1 GB, VGA: _Nvidia 7300 GS_.
   1. In Additional Drivers, I installed version: Current (Recommended) but everything froze and I had to reinstall Ubuntu. I installed version: 173 but I couldn't change the resolution and I had to remove it. What version should I install?
   2. I don't know where's the audio drive version for Linux to download.
   3. I installed Game: Savage 2 by following this steps:
```
mkdir ~/.Games
cd ~/Desktop
chmod +x Savage2Install-1.5.0-x86_32.bin
./Savage2Install-1.5.0-x86_32.bin
```   Can someone explain this way to me?
   4. After installing the game, I didn't find where's it to play it (_My Ubuntu version: 11.10_). I couldn't find ".Games" file.
   4. I downloaded Adobe Flash from its website and I download a file its extension is .tar.gz How to install it (_Using this file_)?

1. Have you tried running Unity 2D, I was having similar issues with 11.10, but Unity 2D worked fine with the recommended driver

2. I don't understand the question, could you please rephrase.  Are you having trouble with your sound?

3. The *mkdir  *command creates a new folder wherever you tell it too.  If I wrote 

```
mkdir /home/carranty/test
```then I would have created a folder called *test* in my home directory.  Note carranty is my user name, each user has a different folder in /home.  Writing out /home/carranty in full can get boring, so the shorthand ~/ is often used, as is the case in your example. By putting a period in front of the folder (eg .Games) you are creating a hidden folder - very similar to hidden folders in windows. 

Next you use the *cd  *command to change directory to /home/[yourUsername]/Desktop

A security feature of Ubuntu (and linux in general) is that files you download from the net are not executable, they can't run unless you give them permission to.  Thats what the chmod +x command does, it makes the bin file executable. In the last line you are simply running the bin file.

See the man pages for more information about commands
```

man mkdir
man cd
man chmod
```4. It's been a while since I installed a bin file, I'm not sure where it puts the files, try running

```
cd /
find -name Savage*
```that might find it.  Note, it won't have installed it in the .Games folder.  That was a completely redundant step.

5. A tar.gz file is a compressed archive, similar to a zip or a rar file.  To unpack it simply cd to its directory and type 

```
gunzip file
```but replace 'file' with the filename.  There should hopefully be installation instructions within the archive.

---

### Post by UbuBegUsr on 2011-12-05
> **grahammechanical said:**
> You should not need an audio driver for Linux. These are built in. You may need to unmute the audio. Click on the sound icon and tick Unmute. From that menu you can open Sound Settings where you can set the audio device and the input and output devices. You may find that these are also muted. So, look for that as well.

Regards.
[QUOTE="carranty"] 2. I don't understand the question, could you please rephrase.  Are you having trouble with your sound?[/QUOTE]
Sorry, I've sound. I'll read everything you wrote wait as I'm very busy then I'll reply. Thanks for help.

---

### Post by UbuBegUsr on 2011-12-09
Hello, I still need help. I tried to install Nvidia driver which I downloaded from its website for Linux using the same way but I didn't succed and I got this error: ```
bash: ./NVIDIA-Linux-x86-290.10.run: Permission denied
``` The file has this extension ".run". I tried to install Java using the same way and the file was bin but I got the same error. What should I do?
> [https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)I read a lot in this link and I think there's a mistake in the thread which tells us how to compile source code. Thanks for the link.
Forget the sound part. I can hear.

---

### Post by Frogs Hair on 2011-12-09
This PPA may be a better way to get that driver . [http://www.ubuntuupdates.org/ppas/27](http://www.ubuntuupdates.org/ppas/27)

---

### Post by Frogs Hair on 2011-12-09
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
```
```
sudo apt-get update
```
```
sudo apt-get install nvidia-current nvidia-settings
```

---

### Post by UbuBegUsr on 2011-12-09
> This PPA may be a better way to get that driver . [http://www.ubuntuupdates.org/ppas/27](http://www.ubuntuupdates.org/ppas/27)
I installed the current version from Additional Divers but it corrupted the system and everything froze forever. I had to reinstall the system.

---

### Post by aaronsgarage on 2011-12-09
Just wishful thinking...Won't it be great if Ubuntu will behave like the Widows we are all used to? I love Ubuntu but find it hard to install software or just about do most things...Love the OS though.

---

### Post by winh8r on 2011-12-11
Hi, 
     Nice to see that you have taken the first step away from w*nd*ws.
Ubuntu is a great operating system, and with a little practice and a bit of patience you will become used to the way it works.
If you are looking for software for everyday things it is best to start with the  Ubuntu Software Centre which is at the bottom of the "Applications" menu at the top of your screen, just look through the categories , or search for a keyword and it will show the relevant software packages.
Take a little time to look through the Synaptic Package Manager and learn to install from there too.
As you become more confident , you can use the Terminal and do all your administration tasks and installation using simple commands like "apt-get install <package name>"

The main thing to remember about Ubuntu is that it is not w*nd*ws , and is not ever going to be like it either, what it is in fact is a gateway to a world where you are in charge of the operating system and not the other way round as you have been accustomed to.

This forum is populated by a large number of very accomplished and experienced users, developers and experts who will have seen and solved almost every possible issue and problem you could ever encounter. If there is something you have an issue with have a quick search through the relevant topic and you will almost certainly find a solution or a workaround in a very short space of time. 
I switched to Ubuntu about 4-5 years ago and have never regretted it one bit, the first few months were a bit confusing , but if you stick at it you will soon find yourself learning a lot ,very quickly.

Try to get someone you know to try Ubuntu as well, and that way you can support each other and share knowledge.

it will not be long before you feel the sense of freedom rising within you!

Good luck

---

### Post by UbuBegUsr on 2011-12-12
> **aaronsgarage said:**
> Just wishful thinking...Won't it be great if Ubuntu will behave like the Widows we are all used to? I love Ubuntu but find it hard to install software or just about do most things...Love the OS though.
It's a different OS. The beginning's a bit confusing. Now, what about my problem???

---

### Post by UbuBegUsr on 2011-12-14
What should I do to install the driver which I downloaded?
[SIZE=2][FONT=Comic Sans MS][SIZE=1]Note: Read the whole discussion to know the problem.[/SIZE][/FONT][/SIZE]

---

