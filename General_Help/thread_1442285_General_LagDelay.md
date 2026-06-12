---
title: "General Lag/Delay"
date: 2010-03-29
forum: General Help
---

### Post by deviator on 2010-03-29
i'm running ubuntu (32bit) on a quad core compaq presario with 3.9gb of ram and a 500gb HDD.

sometimes when i have few windows open (nautilus, firefox) and i'm watching a movie the hard drive will spin up for no reason and everything on screen will hang for a few seconds.

i did a hard drive check and everything seems to be ok there. i have a geforce 8600 gt with the recommended 185 driver installed.

i'm wondering what the problem is? could it be hardware?:popcorn:

edit::
i've noticed this is happening from time to time, no matter what i'm doing. First the computer beeps then the hard drive speeds up and everything lags.

---

### Post by uRock on 2010-03-29
Have you opened a terminal and run top when the problem starts. To run this command just open a terminal and enter ```
top
``` To freeze the monitoring press ```
q
```

---

### Post by kooldino on 2010-03-29
You're not running a WD Green hard drive per chance, are you?

It sounds like some sort of interrupt issue.

---

### Post by kooldino on 2010-03-29
> **iRock said:**
> Have you opened a terminal and run top when the problem starts. To run this command just open a terminal and enter ```
top
``` To freeze the monitoring press ```
q
```

Not sure that would help him since once it freezes nothing responds.

Unless maybe he started running it in advance and then provoked the issue?

---

### Post by deviator on 2010-03-29
i have a blue western digital hard drive but it's not plugged in atm.

my hard drive is a seagate.

and yes, the computer freezes so no chance of doing anything.

if it helps, the audio in movies keep playing when the the hard drive spins up and freezes everything. then when everything resumes the movie is out of sync and i'm forced to restart it.

---

### Post by uRock on 2010-03-29
> **kooldino said:**
> Not sure that would help him since once it freezes nothing responds.

Unless maybe he started running it in advance and then provoked the issue?

Sounds like the RAM is peaking and maybe there is no swap or it is not working properly.

---

### Post by stinkeye on 2010-03-29
Have you tried changing the swappiness value.
I think the default is 60.

You can change swappiness by doing the following:

gksudo gedit /etc/sysctl.conf

Find the line containing "vm.swappiness=" and change the number to the one you'd like to try.

If you have no "vm.swappiness=" , create one at the bottom of the file.

eg I use 
```
vm.swappiness = 10
```

[_**[COLOR="DarkRed"]SwapFaq[/COLOR]**_]("https://help.ubuntu.com/community/SwapFaq")

---

### Post by deviator on 2010-03-30
i added;
# vm.swappiness = 10

under 

# kernel.maps_protect = 1

what does this do exactly as i had none to begin with.

(swappiness, did i spell that right?)

---

### Post by uRock on 2010-03-30
> **deviator said:**
> i added;
# vm.swappiness = 10

under 

# kernel.maps_protect = 1

what does this do exactly as i had none to begin with.

(swappiness, did i spell that right?)

Swappiness supposedly sets a value for when the system wil start moving memory files to Swap form RAM. The lower the swappines the higher amount of RAM will be used before sending to Swap.

---

### Post by stinkeye on 2010-03-30
> **deviator said:**
> i added;
# vm.swappiness = 10

under 

# kernel.maps_protect = 1

what does this do exactly as i had none to begin with.

(swappiness, did i spell that right?)

Don"t include the # symbol otherwise that line will be bypassed.
You just want
```
vm.swappiness = 10
```

---

### Post by deviator on 2010-03-30
no problems so far, set it to 20

---

### Post by kooldino on 2010-03-30
> **iRock said:**
> Swappiness supposedly sets a value for when the system wil start moving memory files to Swap form RAM. The lower the swappines the higher amount of RAM will be used before sending to Swap.

So he set it up so that it swaps to disk less frequently, thus causing less I/O interrupts?

---

### Post by uRock on 2010-03-30
> **kooldino said:**
> So he set it up so that it swaps to disk less frequently, thus causing less I/O interrupts?

That is what I have read. I have seen arguments debunking this, but apparently it works for the OP.

---

### Post by deviator on 2010-03-30
i left the computer on overnight and when i tried to open a movie file just now it would not start. 

a reset resolved this, i don't know if it's related but it seems so.

haven't encountered the original problem as of yet because i haven't had the opportunity to use the pc for an extended period of time.

---

### Post by kooldino on 2010-03-30
You mean the movie file wouldn't begin playing?  Which player(s) did you try?

---

### Post by deviator on 2010-03-30
swappiness set to 20 and i still encountered the problem.

testing on 10.

i used vlc and totem to try to play the files.

i had firefox open with 4 tabs, klamAV updaing, steam minimised to tray and a movie playing.

all of a sudden while switching from one window to another, pc hangs, hard drive spins up and movie becomes out of sync.

if any of that helps.:-?

---

### Post by deviator on 2010-03-31
after doing this i ran memtest to see if i had a faulty ram stick.

unfourtunantly now all i get when ubuntu starts up is two black panels (top and bottom) that flash really fast. i can only ctrl alt del out...

:-({|=

fun~

---

### Post by kooldino on 2010-03-31
See if you can just run on a single stick of RAM.

---

