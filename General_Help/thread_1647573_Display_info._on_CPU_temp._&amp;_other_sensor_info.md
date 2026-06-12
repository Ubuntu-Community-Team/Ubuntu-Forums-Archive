---
title: "Display info. on CPU temp. &amp; other sensor information?"
date: 2010-12-17
forum: General Help
---

### Post by XEtedBear on 2010-12-17
Is there a Linux application which can display motherboard and CPU sensor information and which also satisfies one other, absolutely key, requirement:

It should be directly usable, after installation, by a reasonably intelligent computer application user. That is, it does NOT require deep internal knowledge of specific hardware or obscure system software customisation. It does not require hours, days or weeks of reading of documentation which is so crafted as to be the antithesis of end-user guides. It must be capable of being invoked easily.

This eliminates all software that the Ubuntu Software Centre lists when performing a search with the term 'sensors', with the exception of xsensors. All other software listed with this search installs without error but is then totally invisible to me - not even listed under 'installed software'.

I am aware a key requirement to be a Linux developer is an advanced commitment to play games of 'I bet I can make my software harder to use than yours', but I'm too old for that now. I don't have a need to prove how technically capable I am.

Xsensors installs and tells me where it can be found, but is inadequate as it lists only 2 CPU core temperature readings. It does not give me any indication of motherboard temperature  or fan speeds. That's all I want to do  - get a simple snapshot of sensor values without having to resort to entering BIOS setup. It's the sort of information that is so easily available using the ASUS-supplied 'asus-probe' software under Windows.

Is it possible, given the key requirement previously mentioned?

---

### Post by WarrenSH on 2010-12-17
Bump Bump..

I guess you can look into using [http://www.http://conky.sourceforge.net/](http://www.http://conky.sourceforge.net/)

Bump Bump Bump

---

### Post by nm_geo on 2010-12-17
You might also considered lm-sensors and the gnome applet ..

Screen shot of mine in Lucid 10.04. The applet is shown just above the software screen shot it constantly shows fan speed , cpus and core temp with alarms that are user set. My single laptop fan was just about to stop when I took the pictures as the temps were about 40C.

---

### Post by dcstar on 2010-12-17
> **XEtedBear said:**
> 
........
Xsensors installs and tells me where it can be found, but is inadequate as it lists only 2 CPU core temperature readings. It does not give me any indication of motherboard temperature  or fan speeds. That's all I want to do  - get a simple snapshot of sensor values without having to resort to entering BIOS setup. It's the sort of information that is so easily available using the ASUS-supplied 'asus-probe' software under Windows.


After installing the **lmsensors** & **sensors-applet** packages, it takes all of 5 minutes to add the Hardware Sensors Applet to a panel and configure it.

---

### Post by kgarbutt on 2010-12-17
check out gkrellm and conky

---

### Post by kgarbutt on 2010-12-17
check out gkrellm and conky

---

### Post by Foxcow on 2010-12-17
I have not been able to get conky working the way I want it so I just installed the applet sensors on the toolbar.  It works like a charm.

---

### Post by XEtedBear on 2010-12-19
> **nm_geo said:**
> You might also considered lm-sensors and the gnome applet ..



Thanks for the suggestion, and yes, I did.

Firstly the Gnome applet is installed - but where is it? I gave up after the first 30 minutes of looking. AS I said in the original post, it is NOT listed in the installed applications. That makes it useless - for me when I can't find the application.

(And I notice that this is a common fault with Linux apps installed from  package - they frequently give no indication of where they have been installed, nor how to invoke them).

I spent more than an hour looking at the *m_sensors documentation. It was incomprehesible to me. Above all there was nothing that I could use which said how this colllection of code is to be used. 

By the way, again as is common with things linux, it is VERY difficult for me to figure out the difference between lower case letter l, upper case letter I, number 1, lower case letter i or the piping symbol | on my system. And that's not because of a poor quality display (Iiyama Vision Master Pro 18" plus Mitsubishi Diamond Pro 19"). It's  a result of poor font design, exacerbated by old age. Linux, using case sensitive commands and options, punishes me frequently for this inability.

---

### Post by XEtedBear on 2010-12-19
> **Foxcow said:**
> ... so I just installed the applet sensors on the toolbar.  It works like a charm.

And exactly how did you do that?

Sorry but this is a little too vague. Which toolbar, in which application? In my configuration I seem to have many toolbars - Open Office having one for each major application component for example.

---

### Post by XEtedBear on 2010-12-19
> **dcstar said:**
> After installing the **lmsensors** & **sensors-applet** packages, it takes all of 5 minutes to add the Hardware Sensors Applet to a panel and configure it.

OK, but what is the specification for the skill, knowledge and experience level of the installer who can do this job in 5 minutes? And where are the end-user instructions for so doing?

I am mindful that when I want to use the most complex/complicated functions in my car - the sat. nav system (which, on my older car, is regarded as not well designed) - the interface I am required to use is so presented that I can learn how to activate new features while concentrating on driving the car. I do not need to go to multiple locations (I'm trying to create an analogy for the internet here), gather bits and pieces, ensure they are compatible, discover that they aren't, go somewhere else to get advice on where to find a piece which is compatible, access a multiplicity of dictionaries to decipher the meaning of undefined technical terms which are unknown to me and unused by application end-users, translate text written by technicians for even better informed technicians (who, by definition, don't need it), then assemble all this stuff before finding out that it won't work on my system because of some undisclosed requirement or compatibility issue.

Really all I need is  a simple, straightforward application.

---

### Post by XEtedBear on 2010-12-19
> **XEtedBear said:**
> 
Xsensors installs and tells me where it can be found, but is inadequate as it lists only 2 CPU core temperature readings. I


Now that I think about it, why is xsensors showing TWO CPU core temp. readings? I don't have a dual core CPU (at least, not to my knowledge). BIOS setup shows a single value only.

---

### Post by P1C0 on 2010-12-19
> **XEtedBear said:**
> OK, but what is the specification for the skill, knowledge and experience level of the installer who can do this job in 5 minutes? And where are the end-user instructions for so doing?

I am mindful that when I want to use the most complex/complicated functions in my car - the sat. nav system (which, on my older car, is regarded as not well designed) - the interface I am required to use is so presented that I can learn how to activate new features while concentrating on driving the car. I do not need to go to multiple locations (I'm trying to create an analogy for the internet here), gather bits and pieces, ensure they are compatible, discover that they aren't, go somewhere else to get advice on where to find a piece which is compatible, access a multiplicity of dictionaries to decipher the meaning of undefined technical terms which are unknown to me and unused by application end-users, translate text written by technicians for even better informed technicians (who, by definition, don't need it), then assemble all this stuff before finding out that it won't work on my system because of some undisclosed requirement or compatibility issue.

Really all I need is  a simple, straightforward application.You right click on the gnome panel, then click add to panel and pick 'hardware sensors monitor'.

---

### Post by P1C0 on 2010-12-19
> **XEtedBear said:**
> Now that I think about it, why is xsensors showing TWO CPU core temp. readings? I don't have a dual core CPU (at least, not to my knowledge). BIOS setup shows a single value only.You may have a hyper threading core :)

---

### Post by XEtedBear on 2010-12-19
> **P1C0 said:**
> You right click on the gnome panel, then click add to panel and pick 'hardware sensors monitor'.

Hah! You can't fool me - you measured the time, didn't you? It took just under 5 minutes, discounting local relativistic distortions caused by the fact that I was moving around the room a bit to keep warm.

Many thanks for this guidance.

---

### Post by XEtedBear on 2010-12-19
> **P1C0 said:**
> You may have a hyper threading core :)

Yes, I believe that the Socket 939 AMD Athlon 64 3700+ is such a design. But if both sensors are embedded in the core, why would they provide different (about 1 to 2 degrees C) readings when they are within a few Angstrom units of each other?

---

### Post by Foxcow on 2010-12-19
> **XEtedBear said:**
> Yes, I believe that the Socket 939 AMD Athlon 64 3700+ is such a design. But if both sensors are embedded in the core, why would they provide different (about 1 to 2 degrees C) readings when they are within a few Angstrom units of each other?

The only thing I can think of is that though they are similar, they are not the same.

---

