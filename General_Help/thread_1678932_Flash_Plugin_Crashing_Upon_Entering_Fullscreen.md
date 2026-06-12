---
title: "Flash Plugin Crashing Upon Entering Fullscreen"
date: 2011-01-31
forum: General Help
---

### Post by TheHackOps on 2011-01-31
Hey Guys well I'm on the other side of the bench today, now i try to fix my own problems as much as i can but this one has be stumped.

So recently i kicked a ball (tennis) into my computer which at the time did not have its side panel on. in turn said ball hit the Graphics cards fan and boom goes the dynamite. Now i didn't really care because i have the same GPU onboard (I upgrade my mobo more than my Graphics card) so i decided until i get a new card i will just use the HDMI onboard

Well sure enough this had problems but not drastic ones and because ubuntu is smart it told me what needed to be fixed, I was told to put the system into Low Level Graphics mode in order for the system to recover. Sure enough this worked perfectly and upon booting in i changed my systems graphics over to the onboard and i can play all forms of media except flash in full screen A OK!! even 1080P HD Video.

Now i know that my system is using the onboard fine but i think that flash player is not reconfiguring it self properly for both Chrome and firefox.

So now you know the history and had some lulz at the expense of my stupidity does anyone know why when i enter a flash video EG Youtube, megavideo ect it crashes instantly and gives no error report or anything of that manner.

PS: I installed FlashAid and tweaked it by changing the setting that said it will fix full screen plugin crashes and this did not help, see my system report for flash attached below :)

CHEERS :p:p:p:p

---

### Post by TheHackOps on 2011-01-31
Bump, Solution would be nice

---

### Post by Frogs Hair on 2011-01-31
If you are using  a 64 bit version of Ubuntu you most likley have 32 bit flash with a wrapper if installed from the software center . This is what I use and have no trouble with fullscreen veiwing.
 
There is a 64 bit linux flash at the Adobe web site , but will require manual installation.
 
I'm not able to veiw the file at the moment because I'm at school and can't download anything and am using XP.
 
Normally a flash crash will include a pop up or at least a message in the error console , without that it is hard to say what may be causing the problem  .

---

### Post by TheHackOps on 2011-02-01
No Official Report but that txt contains the whole crash report and im using 32bit

---

### Post by Krytarik on 2011-02-01
You're flash version is listed in your attached file as:
> Shockwave Flash 10.2 r152mine is:
```
Shockwave Flash 10.1 r102
```I wonder where you got it from!?

If you somehow installed it manually, remove it and install those from the official repo, it's called "adobe-flashplugin".

---

