---
title: "xorg thrashing both cores of cpu, system extremely unresponsive"
date: 2011-05-10
forum: General Help
---

### Post by Deadtrooper on 2011-05-10
Hi, I am running 64bit 10.10. For the last fortnight system has become very sluggish responding to input. Programs greyout and become completely unresponsive for long periods of  time and cpu usage on one or both cores ramps up. As I type it is c.80% on both. System Monitor shows usage on the cores mirroring one another.  top in terminal shows Xorg at 99%. I have attached a screenshot. I have rolled back and/or reloaded the Nvidia graphics drivers to no effect. Thanks in advance. Steve

---

### Post by jerrrys on 2011-05-10
haven't had to purge xorg in a long time, don't even remember the exact method i used but it would be something like this

[http://www.ubuntugeek.com/ubuntu-tiphow-to-removeinstall-and-reconfigure-xorg-without-reinstalling-ubuntu.html](http://www.ubuntugeek.com/ubuntu-tiphow-to-removeinstall-and-reconfigure-xorg-without-reinstalling-ubuntu.html)

more here

[http://www.google.com/search?client=ubuntu&channel=fs&q=reset+xorg+ubuntu&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=reset+xorg+ubuntu&ie=utf-8&oe=utf-8)

---

### Post by Deadtrooper on 2011-05-10
[LEFT]Thanks, why would i need to do this? Reading down the thread, it seems there is a good chance of breaking something else if I do it. Since I am completely in the dark as to what is causing the symptoms (even what they mean) there is a good chance, even if doing this cures it, it will reoccur. 
I want to find out what is going on and learn something so I don't make the same mistake again. Humor me, I spend 95% of my time in Windoze. Cheers, Steve
 
[/LEFT]

---

### Post by jerrrys on 2011-05-10
i did humor you steve, thats why the second link.  so you could better understand what your getting into:)

---

### Post by Deadtrooper on 2011-05-11
OOOhhhkaaay - what I am getting into is over my head. I shut down X from a terminal, this shuts down the GUI and I then relaunch or is that reinstall X from the command line? Won't it still be buggered? To correct it I have to edit x.conf? To do that I have to be able to interpret and understand the file and know which parameters/lines are wonky and correct or comment them out or add new lines. I backup/save the original before editing and replacing it, so that if I screw up the new file or it doesn't take for some reason, I can reinsert the crippled but mostly working file and start again. Have I worked that out correctly? I will need fuller instructions and commentary, why and what I am doing etc.
If there is something amiss with x.conf I haven't a clue of identifying that or what a working x.conf should look like. I'd like to learn, to not just understand it but grok it.
What is going on and how do I fix it? Thanks for the links, the info either starts to far in and assumes things I don't know, is to scattered for me to assemble or I am being particularly thick. Probably mostly the latter. Thanks for your patience. Steve

---

### Post by sweetleaf on 2011-05-11
Is xorg unequivocally the problem here? It looks like you're viewing flash in firefox... (possibly in multiple tabs?). If I was troubleshooting from your attached top snapshot, I would start by quitting firefox and watching to see how much xorg calms down.

You might also share something more about your hardware setup, though it sounds like you have a capable machine.

---

### Post by Deadtrooper on 2011-05-11
Thank god for netbooks.[I] ..wrote too soon, something screwy with the keyboard. Ah well, that's another hunt.
You might be onto some thing with Firefox, turning it[/I] off has calmed it down and I recall updating to 4 the other week. I have been used to having umpteen tabs, and sometimes multiple instances, of Firefox open and running for ooh...3 or 4 years now*. Nope...Just launched Cromium, Xorg 97% cpu, idle at the homepage. Sa*me mirroring of cores in System* Monitor. Rig is a Compaq desktop, Asus Leonite mobo, (netbook keyboard giving me a £ sign for capital e, it aint my week) e6300 at 1.86 Ghz and an Nvidia 8800GTX stock. Ubuntu 10.10 dual booting with XP sp3.. I have had a better multitasking, more responsive r no name xp1400,rig. This single core Atom jobby is better.Oh the joy:D. *

---

### Post by Deadtrooper on 2011-05-11
Oh and its the 64bit version with 2GB RAM at the moment. Some RAM swapped out to get something else running.. Its my fall-back workhorse, the graphics are out of a q6600 rig that I'm autopsying and I have an X58 that is stubbornly refusing an OS that should be my main machine. 
Even if Xorg is a red herring, I 'd be grateful for more concise info, so I can make better ****-ups in future,:D.
Steve.

---

### Post by Deadtrooper on 2011-05-11
Closed Chromium, cpu at 97% in top. still that mirroring cpu graph in System Monitor. Closed System Monitor, Xorg at 2%, the usage applet in the top is just showing little spikes.. Launched Firefox with all those tabs. And we are off! Xorg going bonkers, but this time usage is  bouncing round about the place. Let's start this you tube thing that is open. Usage levels long periods at 33%.. couple of spikes, greys out for a sec. If i start doing anything more intensive it will become greyed out and unresponsive for minutes at a time or longer. I think I recall reading something about System Monitor being a resource hog, but these symptoms were the reason I opened it and though it might be exaggerating them it isn't the cause, having a browser open seems more contributory. Again, I should emphaisise  I would normally run this exact setup with lots of tabs open in a browser and swapping between half a dozen other running programs, nary a hiccup. Any thoughts? Thanks. Steve

---

### Post by Deadtrooper on 2011-05-13
Bump.

---

