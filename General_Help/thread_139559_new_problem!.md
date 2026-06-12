---
title: "new problem!"
date: 2006-03-04
forum: General Help
---

### Post by s_spiff on 2006-03-04
recently my windows crashed.. and some how it cause some problems on my other hard disk.. a 80 gb which had ubuntu installed... now i tried reinstalling on it..but i couldnt..so i got a new hdd ...replacement..the old one was scrwd... and tried installing
 during the partioning of the hdd [ 1.5 as swap the rest as whatever you call it ] i pressed enter...and it begins partioning ...gets stuck at 33% and then gives a error sayin ..Input/Output error..coudn't read...somethign..can one one tell me what the damn problem be? its very frustrating!

---

### Post by taurus on 2006-03-04
Have you checked the cable to make sure it's still good???

---

### Post by s_spiff on 2006-03-04
yup... its proper..otherwise it wouldn't be detected right?

---

### Post by s_spiff on 2006-03-04
ok i tried instralling again... the error reads :

 "Input Output error during read
  /dev/ide/host0/bus0/taget1/lun0/disc
  ERROR!!!
 "

---

### Post by az_human on 2006-03-04
Could you be having problems with a disk controller on your motherboard?  How did Windows crashing affect your Linux installation?  Maybe it's not an OS or drive problem, but rather a board problem?

---

### Post by handy on 2006-03-05
This kind of thing is a total pain in the Rs, to diagnose.  You need known good hardware to swap for potential faulty hardware.

Start with the cheapest.

First, I would replace the IDE cable.

If you can find another drive to substitute then you can rule out, or confirm a faulty new drive, & yes they do come from the factory faulty.

If the same thing happens with another drive, then you will have to look at a bad motherboard.

Sorry!  :(

---

### Post by s_spiff on 2006-03-05
gosh...not my mother board man! I'll have to get a new eng. to check it out.. but why is that my 120 hdd which has the windows 98/xp dual installed works fine? the cable seems fine.. cuz the secondary slave 80 gb is getting detected... stuff gets copied on it too... and i can partition it on my xp..[ tho when i connect it...xp takes crap load of time to load up! ] ..i'll give it another try..till then if anyone gets a soln. please let me know.

---

### Post by s_spiff on 2006-03-05
I'm going nuts trying to get a soln.. someone help fast...i'm reaching my critical limit... any more frustration and i'll give up on linux all together! and I seriously don want that to happen!

---

### Post by handy on 2006-03-05
Try a live CD

---

### Post by s_spiff on 2006-03-06
i have the live..but some how..i don find it fun ... i wanna really really install this!

---

### Post by handy on 2006-03-06
I meant for testing purposes...

---

### Post by s_spiff on 2006-03-06
it think I located the problem.. i made the 80 gb as the master... completely removed the 120 from the picture...and tried installing again...everything worked fine.. rightnow i'm online ubuntu... any clue how to add CD to the repositories? I mean last time i backed up all the files /setups i had downloaded... i don wanna download all of them again.

---

