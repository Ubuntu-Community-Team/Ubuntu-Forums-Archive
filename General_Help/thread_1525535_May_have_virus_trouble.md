---
title: "May have virus trouble?"
date: 2010-07-06
forum: General Help
---

### Post by Bunnies on 2010-07-06
Upon starting my laptop, at times a loud beeping occurs which is often followed by plus signs appearing incessantly.  My touch pad will stop functioning and I'll need to restart the computer if I"m in Windows (I have a dual boot- Windows + Ubuntu).

Does anyone know a virus like this or what else the problem may be?

**On Windows I have recently installed Kapersky and ran it and though for a time it seemed to at least make the problem more manageable (no beeping, able to delete all of the plus signs though they still came (frequency was lowered)) they're starting to become a major problem again.

***On ubuntu they sometimes appear, but I can delete them and they'll stop.

---

### Post by Leppie on 2010-07-06
not sure, but sounds like a stuck key...

---

### Post by Bunnies on 2010-07-06
No, my keyboard was disabled due to this presumed virus.  I've cleaned out under the keyboard, anyway and unstalled it at some point.

(I have a usb plug in keyboard atm and unplugged it during one of these attacks.  It didn't cease)

---

### Post by Leppie on 2010-07-06
at what point do these "+"s appear exactly?

---

### Post by oaxacamatt1 on 2010-07-06
When ever I see things like this I try to rule out hardware.  I find 9/10 of the time it is hardware related and a faulty 'x', you name it...  But also use chkrootkit and clamav as well.
Cheers,
Matt

---

### Post by Bunnies on 2010-07-07
Thanks for the advice so far.  Update: I'm now having the same exact problem, only now they are 9's instead of +'s.

I have not discovered a trigger for them yet, but when I start my laptop at times a black screen will appear with a flashing underscore and they will appear there as well as in any text boxes in Windows/Ubuntu (once again, I can get rid of them in Ubuntu but not windows).

---

### Post by Leppie on 2010-07-07
this issue is on a laptop, right? and the usb keyboard is not causing this to happen. have you checked the laptop's keyboard?

---

### Post by Bunnies on 2010-07-07
I cleaned out the keyboard on the laptop, disabled it, enabled it again, etc, etc and these signs will continue appearing along with the beeping upon start up.

BTW! This does not occur *every* time I start the laptop up and at times I can go full days without a problem.  Other days I cannot even access windows as my log in password text box becomes full of these signs.

---

### Post by Calash on 2010-07-07
Definitely sounds like hardware.  The timing of these incidents would help.  Do they happen right when you press the power button, after the Windows/Ubuntu screen, or after you get into the operating system?

---

### Post by Bunnies on 2010-07-07
The beeping occurs a few seconds after I push the power button and will continue until I enter Ubuntu or Windows.

---

### Post by Calash on 2010-07-07
Hmmm.

Being a laptop, having the button change, and it being random I am going to guess it is a intermittent short in the keyboard assembly of the built-in keyboard.  It could be on the surface to where a shot of compressed are in the area would clear it up or in the ribbon cable.  The other option would be an issue on the system board, a much more difficult and expensive part to replace.

The good news is no virus...the bad is that the fix is likely going to be a part and possible service visit.

---

### Post by metalf8801 on 2010-07-07
> **Bunnies said:**
> The beeping occurs a few seconds after I push the power button and will continue until I enter Ubuntu or Windows.

is there any kind of a pattern to the beeping? It could be a diagnostic code which would be used to tell you whats wrong 
[http://www.computerhope.com/beep.htm](http://www.computerhope.com/beep.htm)

if there is no patter it could be beeping because you have a stuck key if thats the case is your laptop still under warranty? If it is try to get the keyboard replaced.  If its not under warranty replacing the keyboard is often easy and you can most likely find a new replacement keyboard on ebay but make sure you get the right one for your laptop  

Good luck 
Dan

---

### Post by TBABill on 2010-07-07
Most laptops have an easily accessible plug you can pull to confirm. Since you use a keyboard via USB can you unplug the laptop keyboard for a few days and operate only from the USB? If so, and if the problem does not recur, you can simply order a new keyboard and replace it. They're normally $20 USD or less and very easy to replace once you figure out which parts to remove to get to it. My Acer just requires pulling a plastic cover around the power button and LED's - no tools required. It's a very thin ribbon cable connected to the underside of the keyboard.
 
That's a troubleshooting step I didn't see in your diagnosis and will confirm a bad key, stuck key, dirt making a key stick but not obvious from the top of the keyboard, or defective input from the keyboard with no key depressed. Keyboards are cheap and usually easy. Many YouTube videos or websites with exact steps for your model....Google is your friend in this case. Search by make and model.

---

### Post by oaxacamatt1 on 2010-07-07
Intermittant hardware bugs are the worst and usually take me the longest time to figure out. I find they usually start out slow but escalate quickly.  

Have you done the **chkrootkit** and the **clamav** for 'actual virus'? I never saw any info on that.  You might as well check the software to make sure...

---

### Post by JackAbear on 2010-07-07
Hi!
Before anything else I would check all the vents for
dust keeping air from reaching the tiny fan inside...heat is the biggest enemy of laptops,  and isn't there a heat wave going on right now in your area. ...try keeping enough air space under the laptop and put a big fan on it while you use it ( after cleaning vents of course)... if it still does it, then it may very well be stuck keys or failing memory or anything at all..but be certain to eliminate a simple heat problem first, before spending the big $$$.
 Hope this helps
A bear

---

### Post by JackAbear on 2010-07-07
Almost forgot, nit costs nothing to checK for viruses before spending for nebulous repairs
 superantispyware, malwharebytes, and avira anti-vir, all free-versions, between these three , there is always one that catches it whenever I get malwhare which is rare for me, nowadays..
Been using these for a year and half now, after getting rid of Nothern oops!( spelling)  which would just tell me " your computer had a virus, it is now quaranteened but some system files may have been corupted...Yeah thanks a lot I would say to myself! ... and expensive too.
I just run a scan with those three whenever I think something might have sneaked in.
A heavily fragmented drive can also cause HDD to overheat and cause eratic behaviour...it never ends does it...I could go on and on!
 But one has to  understand how  each one works to learn exactly how to use them effectively.
Rule of thumb is only 1 active anti virus in the tray ( avira ) the other two sit waiting  on desktop  and just used as extra scanning tools.
Or did you know alll this  stuff already??

---

### Post by Serpher on 2010-07-07
If it was a virus, it wouldn't be effecting your Ubuntu partition at all. It's a hardware failure and if the beeping is lasting into GRUB, it's not what's called a POST message and would mean you have a stuck key for some reason.

---

### Post by JackAbear on 2010-07-07
> **Serpher said:**
> If it was a virus, it wouldn't be effecting your Ubuntu partition at all. It's a hardware failure and if the beeping is lasting into GRUB, it's not what's called a POST message and would mean you have a stuck key for some reason.
I do agree with you guys, I was just suggesting a very inexpensive process of elimination because he has a concern for viruses.( it wouldn't affect ubuntu if it where you are right about that.)
But a fan that is prevented from turning normal speed because of dust cakes collected around it, could do nasty things to a laptop, regardless of OS.
I think that between all of us we've pretty well covered all angles.

---

### Post by JackAbear on 2010-07-07
MMM!...two keyboards!...I wonder how each of the OS's would deal with which keyboard is using the driver ( or if 2 drivers)...could it be a IRQ problem?
... never used two keyboards on same PC, I would almost expect some possibility of  PC confusion there.

---

### Post by Leppie on 2010-07-07
> **JackAbear said:**
> MMM!...two keyboards!...I wonder how each of the OS's would deal with which keyboard is using the driver ( or if 2 drivers)...could it be a IRQ problem?
... never used two keyboards on same PC, I would almost expect some possibility of  PC confusion there.
i use 2 keyboards with my laptop as well all the time. but i don't have the beeping, nor the repeated characters... unless my hand is stuck on the keyboard...

---

### Post by JackAbear on 2010-07-08
well , now I** know** it's possible, thanks!
And I envy your quote below: wish it were mine, certainly fits my temperament also. lol[COLOR=Red]


QUOTE "I'm not antisocial. I'm just not user friendly."

[/COLOR]

---

