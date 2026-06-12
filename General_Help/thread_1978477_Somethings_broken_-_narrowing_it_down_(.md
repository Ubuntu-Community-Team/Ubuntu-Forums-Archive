---
title: "Somethings broken - narrowing it down :("
date: 2012-05-11
forum: General Help
---

### Post by Kenneth Masters on 2012-05-11
Ok so I'm not sure how to give a complete and coherent description of things so I'll just jot down the series of events -

PC shutting down at random moments usually while watching a movies or something equally non-eventful
PC continues to act up in similar ways eventually leading to a prompted repair(where it stops you and asks you either to start normally or repair)
Eventually gets stuck at boot screen saying 'no medium"
Thought it was a bad HD, replaced the HD and installed Windows with no problems thought it was good to go
Noticed PC was shutting off, or returning to login screen, or restarting sometimes
Modified power options to make sure it was nothing in there
PC still doing nonsense
Thought it might be the RAM or something
Trying to boot Memtest from my USB after putting data on the disk and changing the boot order in BIOS
Sometimes it gets stuck at boot screen at "Device :01", other times it will proceed with boot only to say theres "no medium" when trying to boot from external device
Gah! :confused:

I'm out of my league here, anyone know what I might be facing here?  Thank you

windows 7

---

### Post by Bucky Ball on 2012-05-11
Not sure what this has got to do with Ubuntu as you seem to be talking about Win 7. You might have better luck in a Win forum if that is the case. Sounds like hardware to me.

Take out the RAM a stick at a time to identify if this is your problem (ie: two sticks, take one out and boot, all good, probably the stick that's out so take out the other one and replace with stick two. All bad then you have identified the problem. But it could be motherboard or likely power supply unit (is it a generic silver box or a quality PSU?).

---

### Post by whatthefunk on 2012-05-11
Im thinking PSU.  What PSU do you have?

---

### Post by Kenneth Masters on 2012-05-11
LOL!  Oh man looks like my problems stretch farther than my computer... The PSU is a beast unit, I don't think it would be that.  Mainly because it will just freeze up and do crazy **** like when I try and play a vid online it will stop it immediately and then shut down the browser, and then act like nothing happened.  That's what lead me to believe it was memory of some sort.  I have 4 sticks of RAM in there, and I was actually thinking about trying the method you described... but I wasn't sure if I could just swap them oout like that.  So if I just turn it off and rearrange those sticks, it will just use whatever it has available accordingly without configuring anything in the OS?  Thank you Linux lol!

---

### Post by Bucky Ball on 2012-05-11
> **Kenneth Masters said:**
> So if I just turn it off and rearrange those sticks, it will just use whatever it has available accordingly without configuring anything in the OS?

Yes.

PSU: What brand, how old? Fluctuating voltage or other things from a dodgy PSU could explain what is happening. If you have a quality PSU it should have safety switches to prevent this kind of thing anyhow, though. 

Start with the RAM and see what happens. Put in one at a time, perhaps, first slot. It will find whatever is in there.

If this is only happening in Firefox(?) then I would be looking at Firefox bugs. Firefox has been, quite frankly, c**p for me on a computer running 10.04 and one running 10.10 for a few months now. 10.10 it just crashes for no particular reason that I can find (and that is it, machine fine, as if nothing happened) but on 10.04 it crashes Ubuntu also, logs you out, and takes you to the login screen. Unfortunately, this version has been rubbish for us.

---

### Post by sammiev on 2012-05-11
> **whatthefunk said:**
> Im thinking PSU.  What PSU do you have?

+1 changed a few now on my main Desk top. Would serious think and check out this option.

---

### Post by ammofreak on 2012-05-12
Hi ):P
I know overheating does strange things too. Are you monitoring the CPU for this?...My Asus gaming laptop had to be shipped back due to over-heating. Symptoms were shut-down, screen blanking out & coming back on, programs shutting down...

---

