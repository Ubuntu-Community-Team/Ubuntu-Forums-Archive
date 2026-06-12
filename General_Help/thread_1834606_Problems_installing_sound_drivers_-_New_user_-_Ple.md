---
title: "Problems installing sound drivers - New user - Please help :3"
date: 2011-08-27
forum: General Help
---

### Post by The_Falcon on 2011-08-27
Hopefully this is in the right board and descriptive enough. I will give more information upon request.


Alright, well I installed Ubuntu yesterday, got LMMS, a working form of java for minecraft, updated, firefox, got flash etc etc. I go to listen to pandora and there is a LOT of static. "Alright.. I just did something wrong with Flash.". At this point I went to play minecraft. Same problem. I try using LMMS. Same problem. So I went to the hardware manufacturer.. Oh wait, may help if I say what hardware.

Creative X-Fi Titanium Fatal1ty Professional Series

I download the official drivers (not to mention that it's more outdated than the ALREADY ancient windows drivers) and look at the readme. I eventually.. well.. Figure out what the heck they're saying with the 2 3-word lines they tell you.

cd Desktop
cd XFi<tab>
make


At this point I already run into problems. 


make[1]: Entering directory `/usr/src/linux-headers-2.6.38-11-generic'
  CC [M]  /home/wuverul/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.o
/home/wuverul/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.c:14:26: fatal error: sound/driver.h: No such file or directory
compilation terminated.
make[2]: *** [/home/wuverul/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.o] Error 1
make[1]: *** [_module_/home/wuverul/Desktop/XFiDrv_Linux_Public_US_1.00] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-11-generic'
make: *** [all] Error 2
wuverul@ubuntu:~/Desktop/XFiDrv_Linux_Public_US_1.00$ 



I try ignoring this and perform "sudo make install" and enter my password as requested.  


Copy module files...
cp: cannot stat `ctxfi.ko': No such file or directory
make: *** [install] Error 1
wuverul@ubuntu:~/Desktop/XFiDrv_Linux_Public_US_1.00$ 




Does anyone else experience this issue? If so, how can I fix this? It is rather annoying considering everything I do takes a lot of audio (I want to try getting into making a soundtrack for my friend's game-in-the-making. BUT since everything I hear is distorted and static/pure crackles it's kinda hard.


My entire system (Other than stuff that won't make a bit of difference)


Gigabyte S-Series motherboard (thats all I can remember)
3 GB DDR2
Nvidia 9600 GT 512 MB
Intel Core 2 Duo 2.2 GHz
Creative X-Fi Titanium Fatal1ty Professional Series
Installed Ubuntu 11.04 through wubi.

---

### Post by The_Falcon on 2011-08-27
Oh. The microphone also does NOT work. Good to know now that I try using it in teamspeak. >.> Nor does my eyetoy's mic. The camera works perfectly, however.

---

### Post by searchfgold6789 on 2011-08-27
Are you sure you are getting the drivers from here?
[http://support.creative.com/downloads/download.aspx?nDownloadId=10792](http://support.creative.com/downloads/download.aspx?nDownloadId=10792)

---

### Post by The_Falcon on 2011-08-27
Yeah, I did. It still refuses to work. I redownloaded 3 times as well due to the chance of losing data during the download. Nothing was lost during the connection.

---

### Post by searchfgold6789 on 2011-08-27
Okay, I've investigated the drivers from that webpage.
Here's what you should do:
Go  to the website I posted earlier. Download the driver and unpack it into  a directory, say, /driver. Extract the files to the directory. Then,
```
sudo apt-get install build-essential
cd /driver
sudo make
sudo make install

```

---

### Post by .... on 2011-08-27
You shouldn't need to compile a driver for X-fi. It's been in ALSA for a while: [http://www.phoronix.com/scan.php?page=news_item&px=NzI3MA](http://www.phoronix.com/scan.php?page=news_item&px=NzI3MA)

---

### Post by The_Falcon on 2011-08-28
Sorry if I sound like an idiot for saying this, but I have NO idea what "ALSA" is o.o

---

### Post by .... on 2011-08-28
If you're not willing to google/learn basic Linux concepts, then maybe Windows is the best choice for you...

---

### Post by searchfgold6789 on 2011-08-29
> If you're not willing to google/learn basic Linux concepts, then maybe Windows is the best choice for you... 	That is a bad thing to say. Compiling is certainly not a basic concept, and there are many numerous arguments to that statement that I could list, but are irrelevant here.
But moving on, since the drivers are obviously installed, I will guide you through compilation. Did you follow the instructions in my post? If there were any errors or output, post back.

---

### Post by .... on 2011-08-29
> **searchfgold6789 said:**
> That is a bad thing to say. Compiling is certainly not a basic concept, and there are many numerous arguments to that statement that I could list, but are irrelevant here.
But moving on, since the drivers are obviously installed, I will guide you through compilation. Did you follow the instructions in my post? If there were any errors or output, post back.
I was referring to the fact that the OP didn't know what ALSA was and wanted someone to tell him/her when it would be faster to Google.

I was also pointing out that the kernel module currently in the Linux tree is newer/better than the one from the Creative site, and that the OP is barking up the wrong tree.

---

### Post by searchfgold6789 on 2011-08-29
> I was referring to the fact that the OP didn't know what ALSA was and  wanted someone to tell him/her when it would be faster to Google.It would also be faster to just say "google it".
Since the already-installed drivers are not working, is there any reason why compiling drivers that are known to work would be harmful/a waste of time?

---

### Post by The_Falcon on 2011-08-30
Edit: Removing text due to misreading a message and making it worse.

---

### Post by The_Falcon on 2011-08-30
I tried what you were saying to do, by the way. Build-Essential was already installed and it is still failing to install the drivers. Same error messages (with slight changes to reflect the new location)

> **.... said:**
> You shouldn't need to compile a driver for X-fi. It's been in ALSA for a while: [http://www.phoronix.com/scan.php?page=news_item&px=NzI3MA](http://www.phoronix.com/scan.php?page=news_item&px=NzI3MA)

Also, about this, the sound card technically does "work". It just doesn't work properly.

EDIT: It turns out that it only spazzes when LMMS or Java is running (any of the Javas I've found). When nothing else is running it works perfectly.

EDIT 2: Nevermind, everything is spazzy again.

---

