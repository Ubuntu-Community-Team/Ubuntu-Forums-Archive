---
title: "Civilization V graphics issue.."
date: 2010-10-02
forum: General Help
---

### Post by noveevon on 2010-10-02
as one can see from the screenshot it seems like there is something wrong, now i dont know why this is happening, i am currently running most of the settings at high, so its not from a lack of trying..

my specs are:

Intel duo: E5200 2.5gz
Ati Raedon 4850HD
3gb RAM
400 chiftec PSU  (i saw on another thread that its recommended to have atleast 450PSU for my ati card, but so far ive not had any problems)

my graphics card at 25% fan speed is currently around 50-55c so its not that hot..

could it be some driver issue?

PS: iknow its not a Ubuntu specific problem, but i thought it might be connected to Linux and also if other ppl had problems with their graphics via Linux this thread could give them the help they would need ones i get a few replies that is..

---

### Post by filip007 on 2010-10-02
Is that under Wine?

---

### Post by noveevon on 2010-10-02
> **filip007 said:**
> Is that under Wine?


yes...but not full screen..i prefer it like that so i can do other stuff while playing also..

---

### Post by filip007 on 2010-10-03
?

---

### Post by noveevon on 2010-10-03
> **filip007 said:**
> ?


i thought you were referring to my screenshot..

---

### Post by sendblink23 on 2010-10-03
can you tell me the process you did for installing it, so that i can test to see if ti happens the same issue with my 5770

---

### Post by noveevon on 2010-10-04
> **sendblink23 said:**
> can you tell me the process you did for installing it, so that i can test to see if ti happens the same issue with my 5770

i brought the retail DVD and reset Wine (deleted the wine folder and created a new one) then i just installed it from scratch...i also linked it to steam but i dont think its patched anyhting yet.. i will try patching it tomorrow if there is a patch available..

i think it is a driver issue..i am also now experience some problems with saving the game and today its started to crash from a certain point in the game..its all related to the saving problem...as when i try to save i cannot and i cannot see the former saves ive made etc...

---

### Post by Dustin2128 on 2010-10-04
> **noveevon said:**
> as one can see from the screenshot it seems like there is something wrong, now i dont know why this is happening, i am currently running most of the settings at high, so its not from a lack of trying..

my specs are:

Intel duo: E5200 2.5gz
Ati Raedon 4850HD
3gb RAM
400 chiftec PSU  (i saw on another thread that its recommended to have atleast 450PSU for my ati card, but so far ive not had any problems)

my graphics card at 25% fan speed is currently around 50-55c so its not that hot..

could it be some driver issue?

PS: iknow its not a Ubuntu specific problem, but i thought it might be connected to Linux and also if other ppl had problems with their graphics via Linux this thread could give them the help they would need ones i get a few replies that is.. 
sorry, I haven't picked up civ5 yet, what exactly is the problem? I can't see any real discrepancies from what I assume it should look like..

off hand I'd assume it's an ATI/AMD problem, those cards don't have the best linux support yet.

---

### Post by northrup on 2010-10-04
I agree with the person in the last post.  What exactly is the graphics problem?  I don't see one in the screenshot.  Which makes sense: at least from what I understand, a software-based screenshot program will capture what the computer is sending to the video card, not what the video card is sending to the monitor.  Maybe a photograph of the screen would be more useful.

As for the save problem, where are the save files stored?  It could be a matter of Civilization 5 being confused about where "My Documents" is.  Wine has its own version of Regedit you can use to check your PATH variables within Wine.

Also, does Civ5 use DirectX or OpenGL?

---

### Post by noveevon on 2010-10-05
> **Dustin2128 said:**
> sorry, I haven't picked up civ5 yet, what exactly is the problem? I can't see any real discrepancies from what I assume it should look like..

off hand I'd assume it's an ATI/AMD problem, those cards don't have the best linux support yet.

if you compaee it with this shot:

[http://www.pcgameshardware.com/screenshots/original/2010/09/Civilization_5_directX_11-new-04.jpg](http://www.pcgameshardware.com/screenshots/original/2010/09/Civilization_5_directX_11-new-04.jpg)

on my picture you can see small lines in the texture (ground) etc..

it seems there are no patches available yet so i will just have to make it somehow..

also i notice that if i zoom out i see gray spots when i move around on the map..

---

### Post by noveevon on 2010-10-05
> **northrup said:**
> I agree with the person in the last post.  What exactly is the graphics problem?  I don't see one in the screenshot.  Which makes sense: at least from what I understand, a software-based screenshot program will capture what the computer is sending to the video card, not what the video card is sending to the monitor.  Maybe a photograph of the screen would be more useful.

As for the save problem, where are the save files stored?  It could be a matter of Civilization 5 being confused about where "My Documents" is.  Wine has its own version of Regedit you can use to check your PATH variables within Wine.

Also, does Civ5 use DirectX or OpenGL?


it could be a direct x problem as its meant to be played in 11, but so far i can only use direct x 9..

 i will see if i can fix the saving problem...

---

