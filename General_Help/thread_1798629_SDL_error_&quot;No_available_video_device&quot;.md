---
title: "SDL error: &quot;No available video device&quot;"
date: 2011-07-06
forum: General Help
---

### Post by zero2xiii on 2011-07-06
Hay all,

I have this problem with ubuntu 11.04_64bit running on my Gigabyte Q1585N notbook.

Running ANY sdl dependent application causes this error. When I run for example kdenlive, there is no video preview. Runing it with gksudo it opens and flicker the video preview screen, but any mouse click anywhere on the screen crashes the program.

Running openshot the same error, when running with gksudo it crashes all video and laptop needs to be reset (screen goes completely black with resolution of 640x400 sized cursor, thats all)

I have the lastest nvidie propiertry drivers installed (270.41.06) from the additional driver utillity. I assume this is a driver issue, with nvdia incorectly configure the video devices.

How can this be fixed? All drivers are most up to date according to repositories... I really need to be able to use video edditing software on my laptop.

Any more info required? Please and thanks

---

### Post by gordintoronto on 2011-07-06
How did you install kdenlive? If you used Synaptic Package Manager, for example, it automatically would install dozens of "dependencies." It sounds like you did not take that approach.

---

### Post by zero2xiii on 2011-07-06
Hay again,

Everything was installed with synaptic package manager, including SDL, all the mpeg related stuff, all the ffmpeg stuff.. everything EXCEPT the nvidia drivers which were installed trough the aditional drivers utility..

---

### Post by gordintoronto on 2011-07-06
Well darn, I'm out of suggestions.

Does your notebook have dual video adapters? Sometimes it is Nvidia, and sometimes it is Intel?

---

### Post by zero2xiii on 2011-07-07
gordintoronto,

Video adapters? It has a single video card installed the "NVIDIA® GeForce® GT 335M 1GB."

It does however have a HDMI and VGA out (So I can attach up to 2 additional screens to the same card, totaling to 3 screens).. I'm not sure if this answers your question or not.

I have tried attaching a second monitor through the VGA port and tried it in different modes to see if that might fix the problem (as it should be video out #1 then since it's the second monitor).. But that didn't help.

Should I try un-installing the nvidia drivers? Can this break the system in any way. This laptop is used for my DJ an VJ work. I cant afford it breaking on me now.. haha.. But I really need this SDL error fixed.. :confused:

---

### Post by gordintoronto on 2011-07-07
Sorry, if I depended on a computer for my work, I wouldn't mess around with it ever. Better to have a cheap piece of junk to play around with.

In Canada, I'm pretty sure there are no Gigabyte-branded computers. Thanks for posting the exact model code, so I could have a look at the specs online.

My preference for video editing is Cinelerra, so I have not had to use SDL.

---

### Post by zero2xiii on 2011-07-08
Yea the funny part is it used to work on an earlier installation.. But I had to re-install due to the package manager screwing around (It kept telling me that the package that I want to install is dependend on another package, but a newer version of the dependancy is being installed..) But it never had nvidia drivers installed.. 

I'm going to try to un-install the drivers and see if that works, I doubt if it will break the sound.. Lets hope not ;)

I'll look into Cinelerra aswell, maybe its a better alternative for kdenlive and openshot. Cant wait for the linux version of lightworks though...

---

### Post by zero2xiii on 2011-07-08
Nope, un-installing the nvidia drivers completely broke my graphics... Re-installing them now...

---

