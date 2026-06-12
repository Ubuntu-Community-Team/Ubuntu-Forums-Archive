---
title: "Bad CPU"
date: 2011-02-20
forum: General Help
---

### Post by mitk0o0o0 on 2011-02-20
Hello, I am dual booting Ubuntu with Windows 7, i really like Ubuntu, it just looks sexy and i somewhat got used to it so i'm thinking of sticking with it. :)

But i have a problem.. Mostly when i'm on the computer i play RuneScape, I have installed all the needed java thingies and the game runs fine except it gives me really high cpu usage unlike in win7, on win7 it's around 40% while running the applet and connected to the server. But in Ubuntu it's around 70% all the time, and that's really bad cause it heats my CPU and i'm scared that it may get damaged. :(

My processor is AMD Athlon 64 X2 Dual Core 5000+, running 32bit version of Ubuntu 10.10

Also i forgot to mention that cpu goes up mostly when i'm connected to the runescape server, if i'm running the applet unlogged in to the game it's nothing (around 20%)

Please help me fix this problem as i really want to use Ubuntu from now on but would like to play runescape too.

---

### Post by mitk0o0o0 on 2011-02-20
Bump

---

### Post by 3rdalbum on 2011-02-20
> **mitk0o0o0 said:**
> But in Ubuntu it's around 70% all the time, and that's really bad cause it heats my CPU and i'm scared that it may get damaged. :(

Don't be scared. CPUs are rated to run at 100% forever, basically. CPUs are meant to get warm and they are designed to get as warm as they would get at 100% using their stock cooler.

---

### Post by gradinaruvasile on 2011-02-20
The desktop cpus usually cool well. CPU % usage is irrelevant if you have the temperatures in an acceptable domain.
But monitor the temperature, i have seen some x2 Athlons overheat.
Run sensors-detect from a command line (with sudo) and do all the probing (press enter). Let it add the modules to the modules config file. After that the sensors command will tell you the temps.

---

### Post by mitk0o0o0 on 2011-02-20
> **3rdalbum said:**
> Don't be scared. CPUs are rated to run at 100%  forever, basically. CPUs are meant to get warm and they are designed to  get as warm as they would get at 100% using their stock  cooler.So there's nothing to worry about?


> **gradinaruvasile said:**
> The desktop cpus usually cool well. CPU % usage is irrelevant if you have the temperatures in an acceptable domain.
But monitor the temperature, i have seen some x2 Athlons overheat.
Run sensors-detect from a command line (with sudo) and do all the probing (press enter). Let it add the modules to the modules config file. After that the sensors command will tell you the temps.I use xsensors for the temperatures. Do they display them wrong or something? Btw yeah it's a desktop. Usualy while playing runescape the temperature goes somewhere near 60C like 55-59C.

---

### Post by gradinaruvasile on 2011-02-20
55-60 is not a problem. 65-70 and above is where you should worry.

---

### Post by dino99 on 2011-02-20
[http://ubuntuforums.org/showpost.php?p=9755525&postcount=45](http://ubuntuforums.org/showpost.php?p=9755525&postcount=45)

---

### Post by mitk0o0o0 on 2011-02-20
> **gradinaruvasile said:**
> 55-60 is not a problem. 65-70 and above  is where you should worry.Oh that's good then, but if i play  like 2 hours straight without disconnecting  from rs it'll probably go  to 70 :P




> **dino99 said:**
> [http://ubuntuforums.org/showpost.php?p=9755525&postcount=45](http://ubuntuforums.org/showpost.php?p=9755525&postcount=45)Hmm, i hope that will fix the cpu usage problem.. :S
EDIT: Don't see any difference. :(

---

### Post by LoneWolfJack on 2011-02-20
please post the output of "top" while playing.

---

### Post by mitk0o0o0 on 2011-02-20
> **LoneWolfJack said:**
> please post the output of "top" while playing.what is "top"?

EDIT: Great news! I have just installed OpenGL for my nvidia and DirectX, i set it to OpenGL from the settings in RuneScape and the cpu usage got lower, it is mostly now 40-50% which is quite normal.

---

### Post by 3rdalbum on 2011-02-20
> **mitk0o0o0 said:**
> So there's nothing to worry about?

Nothing. CPUs can go at 100% indefinitely. People "overclock" CPUs to make them run faster than 100% as well, and as long as there's sufficient cooling they can run for years at full tilt with the overclock.

Just make sure that your system is being cooled properly, and you'll be fine.

Modern CPUs such as yours will turn themselves off automatically if their temperature goes too high.

---

### Post by mitk0o0o0 on 2011-02-20
> **3rdalbum said:**
> Nothing. CPUs can go at 100% indefinitely. People "overclock" CPUs to make them run faster than 100% as well, and as long as there's sufficient cooling they can run for years at full tilt with the overclock.

Just make sure that your system is being cooled properly, and you'll be fine.

Modern CPUs such as yours will turn themselves off automatically if their temperature goes too high.It will always turn off, right? Nothing will burn up :P

---

