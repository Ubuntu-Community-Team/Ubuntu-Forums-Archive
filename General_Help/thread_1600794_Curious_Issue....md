---
title: "Curious Issue..."
date: 2010-10-19
forum: General Help
---

### Post by rabideggpies on 2010-10-19
Totally new to Ubuntu and have to admit, never used it before until this last few days or so.
I have taken my time in getting Ubuntu up and running on a spare computer that I have here - it was handed to me 'gratis' because winblows kept crashing and the only cure for the issue was 'install another OS on it'. Which, I eventually did.

It's installed brilliantly and it runs. But it's not using the 1GB RAM thats on the Mobo.. instead, it's using the memory on the gfx card instead - 128Mb of it!
I'm getting more and more certain that the previous owner had someone 'fix' the computer with RAM that wasn't suitable for the machine. Either way, I've tried two lots of RAM in the machine and Ubuntu only sees whats on the gfx card.

So.. is it Ubuntu not recognising the RAM? or is it down to previous owners incompetance? (the sort of person you ask 'whats it running?' and they reply with 'facebook' :-p)
I'm guessing it's the previous owners absolute ineptitude and not Ubuntu. Unfortunately, I don't have another machine to test the theory out on (needs too much work doing on it - no power supply, no hdd, cpu fan missing, no RAM...) 

Sorry for a lengthy first post, but I had to get in as much detail as I could :)

---

### Post by TBABill on 2010-10-19
You can't swap out graphics card memory for system RAM so maybe how you are seeing the available RAM could be the issue? 
 
Type:
```
free -m
```
 
in a terminal window to see how much free memory you have. MEM is the amount of memory and the -m tells it to display in MB.

---

### Post by TBABill on 2010-10-19
Try this to get total system memory:
 
```
dmesg | grep Memory
```
 
Edit: fixed code

---

### Post by rabideggpies on 2010-10-19
Heh.. sorted. Was simpler than I thought it would be too :D
I went into bios and q-flashed it and it's been the answer to the problem - it now sees all the ram (all 1Gb of it) and boots up faster than I could've ever dared hope for :D

---

### Post by rabideggpies on 2010-10-27
And the plot thickens...

The gfx card is nvidia (geforce 5) and for all the trying, it seems there's something going on where I can't actually get the drivers from the nvidia site without it spewing a html file at me.
I've followed the instructions as to what to do, but I just can't get the drivers needed. What I have downloaded has failed spectacularly throwing up error messages (can't remember what they were!) but.. really, should I even bother attempting to get the drivers *anyway* (if but to make a slight graphical improvement on the machine) or leave it?

Either way, the machine does run especially sweetly, but things like youtube videos or flash games don't seem to want to run so well - hence the need to get the gfx drivers anyway... 

Any help offered would be greatly appreciated!

:D

---

### Post by Quackers on 2010-10-27
Have you tried System > Admin > Hardware drivers?

---

### Post by halj32 on 2010-10-27
> **rabideggpies said:**
> And the plot thickens...

The gfx card is nvidia (geforce 5) and for all the trying, it seems there's something going on where I can't actually get the drivers from the nvidia site without it spewing a html file at me.
I've followed the instructions as to what to do, but I just can't get the drivers needed. What I have downloaded has failed spectacularly throwing up error messages (can't remember what they were!) but.. really, should I even bother attempting to get the drivers *anyway* (if but to make a slight graphical improvement on the machine) or leave it?

Either way, the machine does run especially sweetly, but things like youtube videos or flash games don't seem to want to run so well - hence the need to get the gfx drivers anyway... 

Any help offered would be greatly appreciated!


:D

when you download the file from nvidia you must right click on it & use "save as"

---

### Post by rabideggpies on 2010-11-11
Thanks! Got the problem sorted :D

However, when you start talking in code, it goes over my head:P
Only been using Ubuntu a couple of weeks anyway :biggrin:

I've noticed it also has a tv tuner card inside the pc but at the moment I'm not touching it as I don't know what I'm doing ;)
I also have a spare gfx card aswell but can't remember what it is right now :roll:

---

