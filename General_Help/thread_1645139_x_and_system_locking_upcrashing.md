---
title: "x and system locking up/crashing"
date: 2010-12-14
forum: General Help
---

### Post by dylan noktum on 2010-12-14
first of some specs;
kernel 2.6.35-23-generic 
64 bit amd turion dual core
toshiba satellite about 6 months old
4gig ram (oddly only 3.1gig shows up :/)
ubuntu 10.10
ATI GPU
umm thats all i can think of if you need more info just ask and tell me how to get it and i will get it 

alright the problem is every now and then my system locks up and i try things like ctrl+alt+F*n* and ctrl+alt+del and ctrl+alt+backspace but nothing works exsept when hold down the power button for a hard reset and occasionally  somthing else happens that can only be comppared to a BSOD in windows but with out the blue screen it just goes to a screen with vertical grey stripes for 2 seconds ish then reboots 

so i dont have the slightest idea of what it could be tho i think it could be something to do with the graphics chip maybe?

its happened quite a few times both in 10.04 and 10.10

if you want system logs i can attach them when ever

---

### Post by owiknowi on 2010-12-14
looks indeed as an problem with the graphics card.

do you have perhaps ms wx installed? and if so does the same problem occur there as well?

---

### Post by dylan noktum on 2010-12-14
im assuming by ms wx you mean Microsoft windows? if so yeah i have 7 on another partition and it has happened a cupple of times but just assumed it was bsod crashing when i was running python but it happened as well at other times

---

### Post by owiknowi on 2010-12-14
> **dylan noktum said:**
> im assuming by ms wx you mean Microsoft windows? if so yeah i have 7 on another partition and it has happened a cupple of times but just assumed it was bsod crashing when i was running python but it happened as well at other times

Nasty problem.

Computers do sometimes crash, especially with complex applications like GIS, graphics editing, programming (testing scripts) and sum such.
With ms wx it looks more like a build in feature ;) 

This also could be a problem with the installed memory or running to many services in the background.

Maybe the manufacturer of your pc or the software you use, have answers on their website?
In the past I could solve a lot of my hardware troubles through the website of the GIS software in use.

---

### Post by dylan noktum on 2010-12-15
ATI Mobility Radeon HD 4650 is the model of the chip and i couldn't find anything on there website that could help
 
 and i wouldnt put it past M$ to build in something like that

---

### Post by owiknowi on 2010-12-15
and the website from the manufacturer of the pc?

since the problem occurs in both ms wx and ubuntu (linux) you could make sure it's not the software by trying a live cd or install an other distribution ([http://distrowatch.com](http://distrowatch.com) use the search option to select the most suitable os).

or you could just leave at at that and go back to where you bought your pc.
maybe it still has guarantee?

beware of some manufacturers who claim:
"we sold the pc with ms wx. you've installed thus it's not our problem anymore"

depending on the country you live in whether such claim is legal (in the EU most of the time it's not).

---

