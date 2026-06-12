---
title: "Windows question, so SORRY"
date: 2010-04-21
forum: General Help
---

### Post by searchfgold6789 on 2010-04-21
OK, I hope you'all 'll help me with this quick windows problem, I know this is a linux forum, but it's kind of a serious last minute thing I hope you'll understand! :-|
I took the CPU out, while the supply was unplugged, I put it back in, and on startup the screen's black and the button's yellow, not green as if it were black on purpouse or darkened if it were off. Any tips on how to dig myself out of this one?

---

### Post by 2hot6ft2 on 2010-04-21
Nothing I'm sure you haven't already thought of but thermal grease, bent pin, poor contact with heatsink, fan not plugged in or accidentally disconnected something else.

---

### Post by searchfgold6789 on 2010-04-21
funny you mention the fan...its running real loud...

---

### Post by 2hot6ft2 on 2010-04-21
> **searchfgold6789 said:**
> funny you mention the fan...its running real loud...
Maybe it's not straight or it's rubbing against something. That would make it not cool like it should and it would overheat real fast.
I would double or triple check everything before you damage something. It may not be plugged in real good, any number of things.

---

### Post by lyall on 2010-04-21
I have not work in a PC330GL for over ten years.  they were good old PCs.  
Try removing the CPU again and clean the contacts on both motherboard and CPU.  
and try it again
hope your fan is okay, it might be had to replace

good luck and have fun learning

---

### Post by searchfgold6789 on 2010-04-21
Heh heh, they are good, and better when they have windows XP and linux, extra ram, and three hard disks.
But I'm working on my mom's pc! she has like a socket 400 pentium 4 something.
The lever keeping the cpu in was closed when I put the cpu back in after i had taken it out, so i took it out *again,* pulled back the lever, and replaced it and closed the lever. The fan is running at its normal speed now, but still the black screen.

---

### Post by garso22 on 2010-04-21
Is the processor in the correct way? Does the corner of the processor with the triangle match the one on the board?

---

### Post by searchfgold6789 on 2010-04-21
Yeah.
Welcome to the forums, neighbour!!!! :):):)
On other forums, people mention the board clock; I know what this is, but does it really have much to do with the cpu?
Logging out for the night,
 - search

---

### Post by oldfred on 2010-04-22
All sorts of things will prevent system from working. I always managed to loosen some cable somewhere. Those old parallel cables often would come out just enough to look like they were still connected but when you pushed them then went in further. I would double check every connector to make sure it is fully seated.

---

### Post by PRC09 on 2010-04-22
You could try unplugging the power cord,remove the cmos battery for a few minutes and then put the battery back and power up again.I am guessing this will reset the bios.I ran into the same scenario when I changed a Celeron to a P4 and that solved it.......

---

### Post by searchfgold6789 on 2010-04-22
bios battery. no, cmos battery. Is that the round metal watch-power thing in the little holder?

---

### Post by Roasted on 2010-04-22
> **searchfgold6789 said:**
> bios battery. no, cmos battery. Is that the round metal watch-power thing in the little holder?

yup.

---

### Post by HHx66 on 2010-04-22
> The lever keeping the cpu in was closed when I put the cpu back in after i had taken it out, so i took it out again, pulled back the lever, and replaced it and closed the lever.

Sounds like you may have broken a pin off of the CPU or bent it. Before I did ANYTHING else, I'd unplug the system, take out the CMOS battery as stated before, let the system stay unplugged for about 10 mins or maybe a little longer if you want to play it safe, I'd disconnect the Fan/Heatsink, take the CPU out (pull the lever to release it first) then turn it around with a good light source, make sure to handle only by the EDGES of the CPU, and inspect the pins, make sure they are all there, and make sure none are bent. 

I've had this SAME problem before years ago, I had taken out the CPU with a little more force than was necessary by accident (I was replacing the heatsink/fan), I assumed everything was okay, put the CPU back, mounted everything properly, turned on, nothing. Turns out I had broken a pin on the CPU by accident.

Another thing you might want to check is that you didn't jar the memory modules and that they are seated correctly.

---

### Post by searchfgold6789 on 2010-04-22
took battery out, checked pins, double-checked pins, triple-checked pins, but it all back in and ... nothing. fan runs smoothly. And it's onboard graphics if you care to know, and she's had problems with the onboard networking before. But all my graphics cards are pointing in the wrong direction. Is there like a breadboard test I can do fr the cpu?
Trying a different chip,
 - search

---

### Post by QIII on 2010-04-22
Start from the start...

Does the machine POST?  (The beeps from the system speaker give you a  hint.  Some mobos even give a series of beeps to indicate if something  is wrong.)

---

### Post by HHx66 on 2010-04-22
Did you re-seat the memory yet? And do you get any post beep error messages?

---

### Post by searchfgold6789 on 2010-04-22
> **HHx66 said:**
> Did you re-seat the memory yet? And do you get any post beep error messages?

I reseated the memory, all 256MiB of it (windows says ten times that much...hmmm...), and no posts. Just the silent fan humming in poetic solitude.

---

### Post by QIII on 2010-04-22
In the Readers' Digest version of POST the BIOS begins POST when the CPU is reset.  Things like the motherboard, memory and other hardware will be checked.  On a hard reboot, the CPU will request the reset vector from the BIOS on the system flash memory.

Something in that process is not working.

It takes very little current to destroy computer components.  Did you take care to discharge any possible static charge my at least touching the chassis of the machine before you started handling the components?  Before you started putting them back in?

---

### Post by searchfgold6789 on 2010-04-22
does the heat sink count?
and again, is there some sort of breadboard test i could do for the p4?



(Official announcement: you will soon see my ubuntu distro change to xubuntu)

---

### Post by zaphod777 on 2010-04-22
Make sure that the CPU fan is plugged into the correct power connector. A lot of motherboards won't let the machine boot if it doesn't detect the CPU fan. It would also make the fan run very fast and loud if it was connected to a regular fan power connector.

---

### Post by searchfgold6789 on 2010-04-23
There were two tiny rectangular fan-power connectors on the mobo. The fan was plugged into one, I tried the other one and it still didn't work. Will it explode or something it I tried another cpu of the same type???

---

### Post by P4man on 2010-04-23
try removing all ram. Turn it on. It should beep. If it doesnt beep, then the system isnt posting.

Next thing to check: powersupply. May soumd silly, but did you connect the PSU to the motherboard, inlcuding in most cases a 4 or 6 pin black/yellow cable for the cpu? Do you have another PSU  you can try? 

If still no dice, disconnect everything you dont strictly need (hdds, cdrom, any add in cards) and try again.

---

### Post by zaphod777 on 2010-04-23
> **searchfgold6789 said:**
> There were two tiny rectangular fan-power connectors on the mobo. The fan was plugged into one, I tried the other one and it still didn't work. Will it explode or something it I tried another cpu of the same type???

Same type of CPU should work fine. Just be careful about static electricity. I always touch the metal of the case to get rid of any static electricity first. technicaly you should wear a grounded wrist strap but I never do.

---

### Post by dandnsmith on 2010-04-23
Just a thought, prompted by some of the postings:
Did the machine ever beep on startup?
I ask this, having been building a couple of systems based on P3 parts and 10 year old mobos - the beep comes from a speaker, which often was external to the mobo, but sometimes on the mobo (looking rather like a capacitor, being a piezo device).
If there is no speaker, it cannot beep - throwing the whole deduction chain off.

HTH

---

### Post by P4man on 2010-04-23
> **zaphod777 said:**
> Same type of CPU should work fine.

Depends how you define "type". Its not because it fits in the same socket and is also a "pentium 4" or "athlon 64" that it will certainly work. So many different variants with different requirements for voltage, bios support etc its a bit of a minefield. It will *usually* work, and almost never cause harm if it doesnt, but its not a given.. unfortunately.

Its also relatively hard to kill a modern cpu (one with a heatspreader protecting the core,  and with thermal protection to prevent it going up in smoke without cooling)  other than by bending the pins -if you still have one with pins. Anything is possible, but not likely the cpu was destroyed by taking it out and putting it in again.

---

### Post by searchfgold6789 on 2010-04-23
I tried the other cpu, and the fan started acting like my friend DJ after he has had chocolate. No beep.
BUT that CPU *might* not have been working either. The old cpu is back in now.

---

### Post by Jguy on 2010-04-23
search: Have you checked for the existance of a speaker? If it's soldered onto the motherboard, then it will look a lot like a capacitor (cylindrical and black), but with a hole in the middle (and usually a '+' and '-' on the top). If it's external to the motherboard, it's likely connected to a 3 or 4 pin strip, usually near to the BIOS battery or the front panel connectors. No speaker = no beep.

If the CPU is completly toast, then the PC will not POST. If there are errors with the CPU, then it should still POSt (albeit providing an error)

I would check for the existance of a speaker and then force an error, pull out all the RAM and turn the machine on.

---

### Post by no2498 on 2010-04-23
you are using the paste on the heatsink

try diff memory

a bad power pack will do the same

---

### Post by searchfgold6789 on 2010-04-23
Yeah there's a piezo there.
And it beeps when I take the pathetic RAM out.
beep-beep-beep-rest-beep-beep-rest-beep-beep-beep

---

### Post by searchfgold6789 on 2010-04-23
Arghh, you'll hate me for this, but I put the memory back in a different slot and it booted just fine and told me to go into bios and check the time. Sorry for the trouble,
 - search
My next complaint: [http://ubuntuforums.org/showthread.php?p=9164029#post9164029](http://ubuntuforums.org/showthread.php?p=9164029#post9164029)

---

