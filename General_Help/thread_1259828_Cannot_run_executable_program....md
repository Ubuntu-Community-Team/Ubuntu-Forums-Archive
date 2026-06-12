---
title: "Cannot run executable program..."
date: 2009-09-06
forum: General Help
---

### Post by bridgetothesun on 2009-09-06
I downloaded Wormux (a game) from their website and changed the permission in the properties to allow linux to run it as a executable program, but when I double click on it and then click run, nothing happens. 

BTW, it is the .sh file. 


Any help?

---

### Post by cholericfun on 2009-09-06
-did they have any instructions on their web page?

-did you try it via terminal and did it give you any error messages?

---

### Post by bridgetothesun on 2009-09-06
Instructions are not on the website. I did search on these forum and it said to change the permissions and then click run. 

How do I run it from terminal? The thing that bothers me is is that I had another download and it also did run when I clicked run. I wonder what the problem is...

---

### Post by cholericfun on 2009-09-06
> **bridgetothesun said:**
> 
How do I run it from terminal? The thing that bothers me is is that I had another download and it also did run when I clicked run. I wonder what the problem is...

i wonder what it is you're trying to run... :)

in terminal go to the place you got that file

e.g. 
```
cd Desktop
```

and run your file there with a dot-slash
```
./program_to_run
```

---

### Post by hockeytux on 2009-09-06
Wormux can be downloaded and installed via Applications > Add/Remove. Much easier and faster.

---

### Post by bridgetothesun on 2009-09-06
I did install it via Add/Remove but it was a incompatible version when I tried to play a network game.

---

### Post by bridgetothesun on 2009-09-06
So I ran it in terminal and I got this error:

> ! Error in graphic/video.cpp:205 (Wormux 0.8.4) : Unable to initialize SDL library: No available video device

./base/error.cpp:93: Missed assertion "false".
terminate called after throwing an instance of 'CError'
  what():  Error in graphic/video.cpp:205 (Wormux 0.8.4) : Unable to initialize SDL library: No available video device
Aborted


I do have a Intel 4500MHD graphics card on this computer. In hardware drivers, it shows as no propietary drivers installed. Could it be that my graphics card is not working at all? This is strange because I get 1000fps in glxgears. 

Any ideas?

---

### Post by bridgetothesun on 2009-09-06
I just tried to run the .sh file for a 2d graphics driver and the same thing happens. I double click, click run and then nothing happens.

---

### Post by bridgetothesun on 2009-09-07
I installed amd64. I have a P8600 Dual Core processor, could this be a problem?

---

### Post by rockstarrem on 2009-09-07
It could be a problem, but is it telling you you can install proprietary drivers? When you go to System > Administratio > Hardware Drivers.

---

### Post by bridgetothesun on 2009-09-07
I think its just saying that none are installed.

---

### Post by bridgetothesun on 2009-09-07
bump...any ideas?

---

### Post by oldos2er on 2009-09-07
The clue is here: ! Error in graphic/video.cpp:205 (Wormux 0.8.4) : Unable to initialize SDL library: No available video device

 Do you have any libsdl* packages installed? It looks like Wormux depends on several of them.

---

### Post by bridgetothesun on 2009-09-07
I tried it install intel graphics drivers and I get the same problem. Just doesn't run....

---

### Post by oldos2er on 2009-09-07
libsdl* has nothing to do with your video drivers. Here's a list of wormux's libsdl* dependencies. You can search for and install them via Synaptic.

libsdl-gfx
libsdl-image
libsdl-mixer
libsdl-ttf
libsdl1.2debian

---

### Post by bridgetothesun on 2009-09-08
but is there a reason I can't run the graphics drivers installation that I downloaded?

---

### Post by P4man on 2009-09-08
Installing graphic cards drivers is usually very different in linux compared to windows. You normally dont  download an executable file from a website and run it, typically you do not install drivers at all (except for recent ati and nvidia cards-, because they are already in the kernel. 

If you want to check if there is a newer driver, just go to system > administation > hardware drivers. If nothing is suggested there, i suggest you don't try to install anything else unless you know what you're doing, or if its really needed.

As for why wormux isnt starting, Im downloading it now, and will check what it gives, although also here, the recommended way is using add/remove programs

---

### Post by P4man on 2009-09-08
I just dowloaded wormux from their website, and it appears to run flawlessly here (but Im on ubuntu 9.10 Karmic alpha).  Googling for your error does suggest a problem with videodrivers, but if the older version from synaptic did work, then I guess it can't be that.

Perhaps there is a reason they didn't put the latest wormux in the repo's yet?

---

### Post by bridgetothesun on 2009-09-08
I'm going to do a clean install of Ubuntu 9.04 again. This time it'll be the 32bit and not 64bit. Maybe that will help.

---

### Post by P4man on 2009-09-08
> **bridgetothesun said:**
> I'm going to do a clean install of Ubuntu 9.04 again. This time it'll be the 32bit and not 64bit. Maybe that will help.

Doh. Yeah there is good chance that will help. the download is 32 bit, I dont see a 64 bit version on the wormux site.

---

