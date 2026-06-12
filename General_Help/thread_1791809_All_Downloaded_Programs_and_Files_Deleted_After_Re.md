---
title: "All Downloaded Programs and Files Deleted After Reboot."
date: 2011-06-27
forum: General Help
---

### Post by Sgasher on 2011-06-27
Hi, I'm incredibly new to Linux, this is my first time using it. In fact the first reboot I'd ever done too. So I turned my computer off, and when I turned it back on, everything I had downloaded or installed the day before had gone. I'm lost and want to know if there's a way I can get these things back? And I'm pretty worried it's going to happen again... 
Any info needed tell me how to get it and I'll give it to you, but I'm relatively annoyed by this and would like my files back if possible :/ 
Also, sorry if I posted this in the wrong place.

---

### Post by electrojustin on 2011-06-27
Are you sure you didn't download these files and programs while you were on the trial version of ubuntu on the LiveCD (did you take a CD out before reboot)? If thats the case, there will be no way to retrieve those files and progams, but rest assured that won't happen again.

---

### Post by Sgasher on 2011-06-27
I took the CD out when asked during the installation. My disk drive is currently empty and was at the time of restart. :/ Taking a closer look, EVERYTHING was reset. Not just deleted, it's like a fresh install... Weird :|

---

### Post by JKyleOKC on 2011-06-27
Were you still running from the "trial" boot-up when you did the downloading?

If you were, then all of that material was stored in RAM and went away when you turned off the machine. It certainly sounds as if this was what happened.

If you re-booted after taking out the CD and before doing the downloads, then we'll need to show you how to search the drive for them. Let us know more details!

---

### Post by electrojustin on 2011-06-27
Yes that would happen if you were still running the trial ubuntu when you downloaded those programs. My question is was this reboot **imediately** after you took out the CD. If this was actually your first reboot, then this is the first time you have accessed your hardrive with ubuntu. As JKyleOKC said before, all that data was in RAM and was lost as soon as you shut down. Sorry!

---

### Post by Sgasher on 2011-06-27
After I installed, I was shown a black screen with white writing on. It said at the bottom that I must remove the disk and allow it to reboot, so I did, after that I installed things like Chromium, Skype and a few games, Minecraft and Spiral Knights, I also put some of my music on the computer. Turned it off for the night, came back after school, turned it on and I was met with a purple gradient screen, it remained in that state for a long time, with no signs of loading. So I shut it down from the back, and restarted it, could that have contributed? Any other information you need, if so can you tell me how to get it, I'm very new, but I understand some of it

EDIT: 
Ahh, I see well thanks for the help :)

---

### Post by electrojustin on 2011-06-27
Hmmm....so it was really your second reboot. Try opening a terminal and typing the following command replacing "x" with the name of a file you know you downloaded e.g. minecraft.jar
 
```
ls / * | grep x
```
 
This will list every file on the system and search for the filename you specified. If something comes up, follow the pathname to the location of your file. If nothing comes up, try again with another file. If that dosn't work, then I'm afraid you've truly lost those files :(.

---

### Post by Sgasher on 2011-06-27
Doesn't seem to find anything :/ Oh well, I'll just get everything again. Thanks for the help man, much appreciated :)

---

