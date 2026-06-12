---
title: "Blank Process"
date: 2009-10-23
forum: General Help
---

### Post by Unanimated on 2009-10-23
My System Monitor sometimes shows a blank process, sometimes two, as a running process in the list. It claims that it's not taking up any CPU or RAM, but I know it is because my computer runs much better when they're not there. They're not there all the time, but I never do anything different to make them appear or go away. I don't know if it's these processes or other ones causing my computer to suddenly be so slow (when I first installed Ubuntu, it ran better and I've upgraded my computer since to a faster processor and video card, but sometimes it still runs worse than it originally did). My computer used to run games very well, and on Windows it ran games like Unreal Tournament 2004 with ease, even with a slower processor and slower video card. I've since upgraded to a 3.0 GHz processor and a better video card and switched to Ubuntu, but it still runs very slowly. Games like Tremulous run worse now than they did before. I don't know if it's these blank processes that are making my computer so slow, or if it's anything else, but I just want to know how to get rid of these and then see if anything else is causing the problem. How can I do this?

---

### Post by misfitpierce on 2009-10-24
Well if they not showing that they are using CPU or memory then I wouldn't blame them unless its not recording for some odd reason... To kill them just right click them and click Kill Process or End them... That is very odd and I have never seen that yet and I have been using Ubuntu for years and Linux itself for longer(diff distros). 

So did just right clicking them and killing them not work or something? Also you are not running Wine App's or something like that are you?

---

### Post by Unanimated on 2009-10-24
I've tried killing them, an error message shows up saying that there is no process where I'm trying to end one. And no, I'm not running any Wine apps. And the games that I play are native, including UT2004.

---

### Post by Unanimated on 2009-10-24
Also, apparently when there is barely anything running, my CPU is being taken up 100%.

---

### Post by misfitpierce on 2009-10-24
What process is taking up all the CPU is the list to make it 100%? Also when did this start? Possibly after installing something you can remember?

---

### Post by anubhavrocks on 2009-10-24
How about using 'top' instead of system monitor.Its likely that gnome system monitor has a bug.

---

### Post by akakingess on 2009-10-24
Could it be a windows virus that is not doing any damage of course, but just keeps trying to run over and over and over and thus taking up CPU. I am fairly new to Linux so please don't laugh me out of the building, but maybe it would be worth running ClamAV just to see if it is something quirky like that.

---

### Post by anubhavrocks on 2009-10-24
> **akakingess said:**
> Could it be a windows virus that is not doing any damage of course, but just keeps trying to run over and over and over and thus taking up CPU. I am fairly new to Linux so please don't laugh me out of the building, but maybe it would be worth running ClamAV just to see if it is something quirky like that.
Windows binaries do not run on linux directly.

From the terminal run:
top

You can see which process is taking up all the cpu.

---

### Post by blwizard on 2009-10-24
> **akakingess said:**
> Could it be a windows virus that is not doing any damage of course, but just keeps trying to run over and over and over and thus taking up CPU. I am fairly new to Linux so please don't laugh me out of the building, but maybe it would be worth running ClamAV just to see if it is something quirky like that.

Binary files are not compatible across different operating systems or platforms. So windows virus won't be able to run on any linux system.

---

### Post by akakingess on 2009-10-24
> **blwizard said:**
> Binary files are not compatible across different operating systems or platforms. So windows virus won't be able to run on any linux system.

I understand all of that, I just know that there have been situations where a virus may get onto a system (usually running wine) and attempt to run, just to find that it can not do a thing, so it just keeps trying to open or whatever it tries to do, and in some cases will just keep trying until it is deleted. Like I stated, I know it can't actually infect a Linux system, but it could TRY to run and possibly use up resources by just trying.  I am sorry that y'all think that I'm that naive and will just leave this thread to the experts.

---

### Post by blwizard on 2009-10-24
> **akakingess said:**
> I understand all of that, I just know that there have been situations where a virus may get onto a system (usually running wine) and attempt to run, just to find that it can not do a thing, so it just keeps trying to open or whatever it tries to do, and in some cases will just keep trying until it is deleted. Like I stated, I know it can't actually infect a Linux system, but it could TRY to run and possibly use up resources by just trying.  I am sorry that y'all think that I'm that naive and will just leave this thread to the experts.

Sorry no intention to start a fight, but the OP has stated that he doesn't use wine or that sort of stuff, so windows binaries won't even be able to start, how could it use up the system resources?

---

### Post by anubhavrocks on 2009-10-24
If i were to take a guess it must be updatedb or some apt related daemon.But you can easily find that out.

---

### Post by misfitpierce on 2009-10-24
Well he says he not running any Wine apps so I doubt he has anything installed via Wine therefor a virus in Wine is very hard to believe but don't worry about it akakingess, atleast you tried helping which is good to say. As said you could run TOP if gnome system monitor is not showing the app using 100% of cpu... please post what it is.

---

### Post by akakingess on 2009-10-24
> **blwizard said:**
> Sorry no intention to start a fight, but the OP has stated that he doesn't use wine or that sort of stuff, so windows binaries won't even be able to start, how could it use up the system resources?

Sorry, I completely missed the fact that the OP did not use wine, my bad, so I will let y'all get to work and stop getting off topic. Good luck to you all.

---

### Post by Unanimated on 2009-10-24
Well, I have Wine installed, I just rarely use any Windows apps. Sorry for not clearing that up. I'm on a Windows PC right now, I'll try top when I get home.

---

### Post by Unanimated on 2009-10-24
Alright, it was a bug in System Monitor. So thanks to everyone for helping.

---

