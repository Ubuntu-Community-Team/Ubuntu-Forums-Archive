---
title: "Rage Mobility P/M x2 no TV-Out"
date: 2006-03-29
forum: General Help
---

### Post by Paddy1869 on 2006-03-29
Hi

Pretty new at the Linux malarky. But enjoying it so far.

Managed to get my old Compaq Evo N400c running quite nicely except for a couple of issues. Well, a few more than a couple...but anyway :rolleyes: 

I have a Rage Mobility P/M x2 in this ageing machine and t works quite well except the tv-out doesn`t seem to work. I have googled for an answer and haven`t found anything. Any ideas?

Also on bootup I have no sound. If I click the volume button and turn the sound down then up THEN I have sound. Bit annoying, but I can live with it if there is no answer.

Ok, hope someone can help.

Cheers

Paddy

---

### Post by gord on 2006-03-29
you could try atitvout (make sure extra repositorys are enabled)
```
sudo apt-get install atitvout
```

iv not had much look with my rage 128 pro, but who knows :)

---

### Post by Paddy1869 on 2006-03-30
It didn`t work. It installed okay, but didn`t seem to add any extra functionality. Not a big deal as I didn`t used it that often. Just don`t like it when things that should work don`t :)

Still no sound on bootup until I press my volume button.

---

### Post by gigahz on 2008-01-18
HOW IS THIS POSSIBLE?

THAT EASY??? 

Sorry for my captials, but this is definately a thread to bookmark! After weeks of frustration with gatos, fglrx, "No devices detected in xorg.log" etc etc etc ...

this was the solution.
Simply, incredible.

I ran "sudo atitvout detect" (and it returned between other things "TV")
then "sudo atitvout t" (tv display enabled)

I run Gutsy on a Dell laptop with Rage Mobility 128 P/M. And now TV-out WORKS!
I'll use it as a set-top box connected to my tv :) :) :) :) :) :)

thanks a LOT. I'll try and direct more people to this thread:)

---

### Post by www.rzr.online.fr on 2008-01-20
Can you try again on hardy version (pre release) ?
It fails on my IGP320M :
[http://rzr.online.fr/q/TvOut](http://rzr.online.fr/q/TvOut)

---

