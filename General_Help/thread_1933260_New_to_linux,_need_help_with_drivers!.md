---
title: "New to linux, need help with drivers!"
date: 2012-02-28
forum: General Help
---

### Post by Aluwolf on 2012-02-28
This is my first time using linux, I installed Ubuntu 10.04. I have more than one issue so I'm just gonna lay them out and if you know a fix for any of them please help me.

My first and most important question is where the heck do I find drivers for my video card.
I am using a Radeon 6850, i went into the command prompt, and entered some code that was supposed to see if i have drivers for 3D acceleration, i got a no as a reply.
I tried to use the Linux catalyst drivers from AMD, but it asks me for an application to run it with. I choose wine on a whim cause Idk what else there is.

Upon opening it under system i get this error:
 p, li { white-space: pre-wrap; }  There was a problem initializing Catalyst Control Center Linux edition.  It could be caused by the following.
  No ATI graphics driver is installed, or the ATI driver is not functioning properly.
 Please install the ATI driver appropriate for you ATI hardware, or configure using aticonfig.
  



Secondly, it appears that I am not getting video through HDMI, how do i fix this?
Im also getting a monitor unknown when i go to the monitor settings.


Lastly, I cannot get Steam to work for anything, when i try and download a game from steam steam never launches and when i launch it from my computer it appears and says connecting to aluwolf and then nothing happens and it vanishes.


I've tried google, but no one seems to be having the problems I am.

---

### Post by rollinsmoke on 2012-02-28
heres what ive found for ati drivers on ubuntu 11.10

[http://linux-software-news-tutorials.blogspot.com/2011/10/ubuntu-1110-oneiric-problems-with-ati.html](http://linux-software-news-tutorials.blogspot.com/2011/10/ubuntu-1110-oneiric-problems-with-ati.html)


hope it helps

---

### Post by Aluwolf on 2012-02-28
Thats not the version I have installled.

---

### Post by rollinsmoke on 2012-02-29
sudo apt-get install fglrx


this is what i found on ask ubuntu for the 6850 heres the url 

[http://askubuntu.com/questions/68870/how-do-i-install-the-drivers-for-my-ati-6850-graphics-card](http://askubuntu.com/questions/68870/how-do-i-install-the-drivers-for-my-ati-6850-graphics-card)

and the hdmi should work with the proper drivers

---

### Post by mastablasta on 2012-02-29
These drivers should be installed via the hardware drivers menu. 
>  
click System in the top panel,go to Administration and find Hardware Drivers

however since you are using an older version of Ubuntu those that will install might not be the latest ones and you do have a newer GPU. To get the latest ones you need to download linux drivers form ati then follow instructions here:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
 
only you will have to tailor them a bit to your Ubuntu version (oneiric is the latest ubuntu).
 
BTW check my signature for a very nice user manual with pics and all. it iwll help you getting started with the OS.

---

### Post by Aluwolf on 2012-02-29
Few things.

I updated to 10.10 and steam is now working
Also additional drivers is now working but upon installing I get a big ugly watermark in the bottom right corner that says Hardware not supported. Why is this.

Also, the screen goes gray after about 5 minutes of booting now, so i uninstalled those drivers.

HDMI Input appears to be working now, but i cannot achieve 720p.

Most of my issues seem to have gone away just by updating to 10.10, but i really want to use 2 screens and be able to go to a higher screen resolution.

---

### Post by mastablasta on 2012-02-29
in linux drivers are often part of or connected with kernel. higher kernel (newer verison of OS) will have better support for newer hardware.
 
which driver did you install? the one in the menu? as i said they might not be the latest version. latest catalyst is i think 12.1
 
support for linux for these newer card is sort of dripping in. but they are usually fixed and ready until next LTS comes out.
version 10.10 is from October 2010 and it's stupport will run out in April or May this year. Why not use latest stable version 11.10?

---

### Post by Mark Phelps on 2012-02-29
> **PerlongFiona said:**
> I've tried google, but no one seems to be having the problems I am.

Please do NOT hijack this thread for YOUR problem.  That makes problem solving very difficult.  Please start your OWN thread.  thanks

---

