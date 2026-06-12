---
title: "Flash dies inside Firefox after an hour or so"
date: 2009-10-15
forum: General Help
---

### Post by sproaty on 2009-10-15
After Firefox (3 or 3.5, same behaviour in both) has been running for an hour or so, Flash will no longer continue to load and just displays a blank empty space where the video should be.

Latest versions of Flash / Firefox is installed - I always update when apt prompts me to. 

The only fix I've found currently is to restart the browser, but this is really annoying to have to do.


Linux ubuntu 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:48:52 UTC 2009 x86_64 GNU/Linux 

Jaunty 9.04

---

### Post by jbrown96 on 2009-10-15
I would install the 64-bit pre-release version of flash from Adobe. I've been using it since the beginning of 2009, and it's really good. Much more stable than trying to wrap the 32-bit flash from the repositories. Here's the direct download link [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz")
Download it. Then make sure to remove the current version of flash. ```
sudo apt-get remove flashplugin-nonfree
``` Close firefox. Install flash. The file you downloaded is a compressed archive (like a .zip). Right click on it and extract. You should get a file called libflashplayer.so. Cut this file and open up the file browser. go to your home folder, and show hidden files (Control+H I think or in View-->show hidden files). Find the .mozilla folder and open it. Create a folder called "plugins" (without the quotes). Then paste libflashplayer.so inside.

---

### Post by paul.drover on 2009-10-15
What follows might be deemed a silly question, and one that I can guess the answer to, but here it goes anyway:

But what if you are running on a 32 bit machine (yes some of us run linux on older machines because it *will* run on older machines)? Surely the 64 bit flash player will not function. Are we left to stare at a blank screen where the flash should be?

Paul.

---

### Post by sproaty on 2009-10-15
> **jbrown96 said:**
> I would install the 64-bit pre-release version of flash from Adobe. I've been using it since the beginning of 2009, and it's really good. Much more stable than trying to wrap the 32-bit flash from the repositories. Here's the direct download link [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz")
Download it. Then make sure to remove the current version of flash. ```
sudo apt-get remove flashplugin-nonfree
``` Close firefox. Install flash. The file you downloaded is a compressed archive (like a .zip). Right click on it and extract. You should get a file called libflashplayer.so. Cut this file and open up the file browser. go to your home folder, and show hidden files (Control+H I think or in View-->show hidden files). Find the .mozilla folder and open it. Create a folder called "plugins" (without the quotes). Then paste libflashplayer.so inside.


Thanks for the reply, I just done this - only time will tell if it has worked or not. I'll try and see if a youtube video will load in the next hour or so and report back.

oh, I didn't have flash-nonfree installing, by the way. I'm not sure *where* my current Flash came from!

Thanks!

---

### Post by sproaty on 2009-10-15
Nope, it just happened again. Any other suggestions?


[IMG]http://img96.imageshack.us/img96/3388/93414108.png[/IMG]

---

### Post by Johnny B on 2009-10-15
try this script
[http://ubuntuforums.org/showthread.php?t=1233235]("http://ubuntuforums.org/showthread.php?t=1233235")

---

### Post by jwbrase on 2009-10-15
When I installed Ubuntu on our home desktop, I never did manage to get Flash to work properly with Firefox. I ended up looking for other browsers and eventually installed Opera. I found it so addicting that I installed it on the Windows side of the same desktop, plus our other desktop. When I bought my current Ubuntu laptop from System76, it came with Flash and Firefox working perfectly, but I prefer Opera enough that I've hardly ever used Firefox on this machine, even though it works with Flash.

---

### Post by justmehere on 2009-11-03
This happens to me too. I've lost count of the number of times I've reinstalled flash using various advice and I still have the problem. When Firefox is first opened flash video works fine but after a while, sometimes only a few minutes, it will stop working and I just get a blank space as described. Closing every firefox window then restarting it fixes the problem until next time. Any hint of what to check next would be most appreciated.

:¬}

---

### Post by jnew93 on 2009-11-03
I had those same problems, and installing the 64bit alpha from Adobe solved them for me. However, I am running a 64bit machine, so I do not know how to remedy a 32bit problem. :-k

---

