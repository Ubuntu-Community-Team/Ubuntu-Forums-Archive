---
title: "Unable to enumerate USB device"
date: 2009-12-01
forum: General Help
---

### Post by bravo sierra echo on 2009-12-01
During the boot procedure, I'm getting the following error message repeatedly:

xxx Unable to enumerate USB device on Port xxx

Where xxx is a number that increases each time.  Usually it fills half a screen and then stops, but twice now it's carried on apparently forever.  After waiting for it to stop I've ctrl-alt-deleted, which seems to have had the effect of destroying my install down to a Grub error 15.

I'm fairly sure this is a hardware problem as I have seen the same error message when booting from a LiveCD.  This machine has been running fine since I got it in September, but has now started doing this over the last three or four days.

On the external USB ports I have a keyboard, mouse and wireless card, all of which seem to be working fine.  On the internal one I have a card reader, which intermittently doesn't seem to work - it seems to not work for a while after the machine is switched on, then come back to life.  I have tried booting the machine without the card reader plugged in, and still get the error messages.

Once the computer has successfully booted, everything works absolutely fine - my issue is with these error messages interrupting the boot process.

The computer's battery seems to have gone - I normally unplug it overnight, and have noticed the time reset itself from 00:00 on 01/01 when the internet connection kicks in.

One of my two hard drives is failing, with 300 bad sectors.

My questions are:

Could one of these problems be causing the error messages - ie would a new battery and/or hard drive cure it?

Is there a way to suppress the error messages so that the machine can boot properly?

I'm running Ubuntu Karmic Koala, all up to date.

---

### Post by Bunnybugs on 2009-12-01
> **bravo sierra echo said:**
> During the boot procedure, I'm getting the following error message repeatedly:

xxx Unable to enumerate USB device on Port xxx

Where xxx is a number that increases each time.  Usually it fills half a screen and then stops, but twice now it's carried on apparently forever.  After waiting for it to stop I've ctrl-alt-deleted, which seems to have had the effect of destroying my install down to a Grub error 15.

I'm fairly sure this is a hardware problem as I have seen the same error message when booting from a LiveCD.  This machine has been running fine since I got it in September, but has now started doing this over the last three or four days.

On the external USB ports I have a keyboard, mouse and wireless card, all of which seem to be working fine.  On the internal one I have a card reader, which intermittently doesn't seem to work - it seems to not work for a while after the machine is switched on, then come back to life.  I have tried booting the machine without the card reader plugged in, and still get the error messages.

Once the computer has successfully booted, everything works absolutely fine - my issue is with these error messages interrupting the boot process.

The computer's battery seems to have gone - I normally unplug it overnight, and have noticed the time reset itself from 00:00 on 01/01 when the internet connection kicks in.

One of my two hard drives is failing, with 300 bad sectors.

My questions are:

Could one of these problems be causing the error messages - ie would a new battery and/or hard drive cure it?

Is there a way to suppress the error messages so that the machine can boot properly?

I'm running Ubuntu Karmic Koala, all up to date.


As far as I know, the battery supports some stuff like a chip for the USB-guide... that chip gives you the option to use the USB drive while you are booting... But, it's stupid to unplug a computer overnight... Your system ain't dangerous when it's plugged in... Just remember that... It won't set fire, explode, or whatever you think...

It's an unknown error to me as well... Been looking on the internet, but didn't find any answers... (even not on background sites about linux that aren't google indexed)

Replace the system battery, and yeah, the damaged sectors on the harddrive worry me to!... Go to some geek with a store, and let him take a look at the hard-drive!

---

### Post by bravo sierra echo on 2009-12-01
I have found other forum posts with people having the same problem, but unfortunately no solutions!

The hard drive is going to have to wait until after Christmas (bit broke this month) but I will sort out the battery asap.

I know it's "safe" to leave the computer plugged in, but it is still drawing power - I unplug it to save on my electricity bill and while I know it is only a few pence I really am that tight-fisted!

---

### Post by Bunnybugs on 2009-12-02
> **bravo sierra echo said:**
> I have found other forum posts with people having the same problem, but unfortunately no solutions!

The hard drive is going to have to wait until after Christmas (bit broke this month) but I will sort out the battery asap.

I know it's "safe" to leave the computer plugged in, but it is still drawing power - I unplug it to save on my electricity bill and while I know it is only a few pence I really am that tight-fisted!


Your computer uses when shutted down, about 0.1mA... depending on your powergrid, that makes:

230V x 1A x 1h = 230KWh
115V x 1A x 1h = 115KWh

230V x 0.0001A (0.1mAx1000=0.0001A) x 24h = 0.023KWh
115V x 0.0002A x 24h = 0.023KWh 
(Volt(V) x Ampere(A) x Time(h) = Powerconsumption (KWh))

1KWh : 0.023KWh = 43days with 1KWh


1 Kwh cost about €0.20, 0.30USD



Why are you saving money with these numbers... what help do you have from these amounts of money? I really think that a computer battery is more expensive;)

Don't try to be a cheap *******, because it just costs more in stead of saving money!

---

### Post by bravo sierra echo on 2009-12-03
Anyway...

I don't expect hardware diagnosis across the internet, but I was hoping someone could answer this part:

Can this error message be suppressed, so that the machine can boot cleanly?  Whatever is wrong, the machine works perfectly well once it has managed to boot.  Does anyone know?

---

### Post by Bunnybugs on 2009-12-03
> **bravo sierra echo said:**
> Anyway...

I don't expect hardware diagnosis across the internet, but I was hoping someone could answer this part:

Can this error message be suppressed, so that the machine can boot cleanly?  Whatever is wrong, the machine works perfectly well once it has managed to boot.  Does anyone know?


Do you have a LiveCD??

If you do, boot from the liveCD, and find out what happens with your harddrive

---

