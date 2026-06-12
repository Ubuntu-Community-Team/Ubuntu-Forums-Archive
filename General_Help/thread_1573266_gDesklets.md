---
title: "gDesklets"
date: 2010-09-12
forum: General Help
---

### Post by AGNKim on 2010-09-12
I installed gDesklets using Synaptic. It seemed to install fine. When I click on it (Applications > Accessories > gDesklets), I see where it is trying to start up at the bottom of my screen. It sits there a few seconds, the cursor is spinning, as if its loading, then it just goes away. The program never starts. The cursor goes back to normal. But the gDesklets never initiated.

I searched and found someone with similar problems (though not the same), but the solution referred to something that I had no idea what was being discussed. (FYI: I'm a very new Ubuntuian).

Any suggestions?

Thanks,
Kim

---

### Post by sxmaxchine on 2010-09-12
I have the same problem and never found an answer.

Instead i just installed screenlets, it does basicaly the same thing

---

### Post by Ghost_Mazal on 2010-09-17
Have the same problem and also can't find a solution

---

### Post by ean5533 on 2010-09-17
I'm not familiar with gDesklets but I'll try to help. Do a couple things for me:

1) Run the program from a terminal and post anything interesting that it spits out. To do this, open up a terminal (Applications->Accessories->Terminal) and type...

```
gdesklets
```

...and then press enter.

2) Post a link to the solution you found that you weren't understanding. Maybe one of us will know what it was talking about.

---

### Post by Ghost_Mazal on 2010-09-17
Mine says this:

```
mazal@ubuntu64:~$ gdesklets
Starting gdesklets-daemon...
Connecting to daemon [ ###         ]
==========================================================[09/17/10-15:51:57]===
Could not import tiling module!

Cannot establish connection to daemon: timeout!
The log file might help you solving the problem.
mazal@ubuntu64:~$ 
```

---

### Post by ean5533 on 2010-09-17
> **Ghost_Mazal said:**
> Mine says this:

```
mazal@ubuntu64:~$ gdesklets
Starting gdesklets-daemon...
Connecting to daemon [ ###         ]
==========================================================[09/17/10-15:51:57]===
Could not import tiling module!

Cannot establish connection to daemon: timeout!
The log file might help you solving the problem.
mazal@ubuntu64:~$ 
```

I found something that might be related to your specific problem:

[http://forum.linuxmint.com/viewtopic.php?f=90&t=32554](http://forum.linuxmint.com/viewtopic.php?f=90&t=32554)

However, it's an old post so it may not be relevant anymore. Also, that post mentions another command that might help to further diagnose any problems:

```
gdesklets check
```

Give that a try if the first fix doesn't work.

---

### Post by dkjMusic on 2010-09-23
The link posted by ean5533 above ([http://forum.linuxmint.com/viewtopic.php?f=90&t=32554](http://forum.linuxmint.com/viewtopic.php?f=90&t=32554)) worked for me. After making the changes to /usr/lib/gdesklets/utils/ErrorFormatter.py specified on that page, running Applications/Accessories/gDesklets opened gDesklets Shell from which I could select and run the desired desklets.

If this works for you (hope so), maybe mark the thread as Solved?

---

### Post by elliotn on 2010-09-23
> **Ghost_Mazal said:**
> Have the same problem and also can't find a solution

same problem here

---

### Post by ean5533 on 2010-09-23
> **elliotn said:**
> same problem here

Did you try reading the links I posted? Or the commands I posted?

---

### Post by æøå on 2010-09-23
Same problem!

---

### Post by alcamus on 2010-11-01
ean5533's solution worked for me without a hitch.

---

### Post by tommy1987 on 2010-11-08
> **dkjMusic said:**
> The link posted by ean5533 above ([http://forum.linuxmint.com/viewtopic.php?f=90&t=32554](http://forum.linuxmint.com/viewtopic.php?f=90&t=32554)) worked for me. After making the changes to /usr/lib/gdesklets/utils/ErrorFormatter.py specified on that page, running Applications/Accessories/gDesklets opened gDesklets Shell from which I could select and run the desired desklets.

If this works for you (hope so), maybe mark the thread as Solved?

Worked for me

---

### Post by rockstarrem on 2011-02-07
Don't want to bump this topic, but since it shows up in Google I thought I'd say that the link that ean5533 posted has worked for me perfectly... [http://forum.linuxmint.com/viewtopic.php?f=90&t=32554](http://forum.linuxmint.com/viewtopic.php?f=90&t=32554)

---

### Post by LoneWolf_53 on 2011-03-10
Deserves a bump, it's the only thing that worked for me as well in Maverick.

---

### Post by mitk0o0o0 on 2011-03-11
> **ean5533 said:**
> I'm not familiar with gDesklets but I'll try to help. Do a couple things for me:

1) Run the program from a terminal and post anything interesting that it spits out. To do this, open up a terminal (Applications->Accessories->Terminal) and type...

```
gdesklets
```...and then press enter.

2) Post a link to the solution you found that you weren't understanding. Maybe one of us will know what it was talking about.Really sorry for gravedigging but i really want those gadgets. I went to the link ean5533 gave, followed all the instructions but at the end i don't have the "ErrorFormatter" file anywhere. Tried search function to find it and still it's not there in /usr/lib/gdesklets (even the whole folder isn't there but i do have gdesklets installed) please help.

Running ubuntu 10.10 32bit (maverick i think)

---

