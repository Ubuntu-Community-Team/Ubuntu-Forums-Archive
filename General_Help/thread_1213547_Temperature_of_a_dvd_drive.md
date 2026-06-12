---
title: "Temperature of a dvd drive"
date: 2009-07-14
forum: General Help
---

### Post by M4rotku on 2009-07-14
Hey guys,

Can anyone give me a command that returns the temperature of a dvd drive assuming that the drive is '/dev/dvd'?

I need it to make sure that a program I am writing does not overheat the dvd drive.  (I may have already lost one casualty (drive) in trying to develop this.)

Also, can anyone tell me what is a safe temperature for the dvd drives?  Or, in other words, at what temperature should I pause the program so that the drive can cool off?

Much thanks,
M4rotku

---

### Post by PGScooter on 2009-07-14
you've probably heard/used it, but in case not, conky gives a lot of info. Maybe it could give the dvd temp.

---

### Post by M4rotku on 2009-07-15
Conky gets those by using a command for each thing that it receives.  I'm looking just for the command.  Though, I guess if I can find it in Conky, then I can try to figure out how they got it.

Any other ideas?

Much thanks,
M4rotku

---

### Post by M4rotku on 2009-07-16
bump

---

### Post by M4rotku on 2009-07-18
bump

---

### Post by Whiffle on 2009-07-18
I don't believe I've ever seen a DVD drive with a temperature sensor in it.  If there were, I should think smartmontools might pick it up.

---

### Post by 3rdalbum on 2009-07-18
Funnily enough, I was reading the hdparm manual page the other day and saw the option. Not many drives have temperature sensors - it's mostly Hitachi drives.

The command is:

```
sudo hdparm -H <device>
```

where <device> is the device whose temperature sensor you want to read.

None of my drives support it.

I wasn't aware that you could do anything to a DVD drive to overheat it anyway.

---

### Post by moster on 2009-07-19
Every new HDD have temp sensor. NONE of DVD drives have temp sensor. If you keep low temp inside case with fans, there should not be overheating.

If you really want that, only thing you can do is to buy external sensors. I have one that go instead of floppy. There is little LCD screen and I have two temp sensor diode that I can put on HDD, DVD, or just leave it in case to see my internal temperature. :)
[URL="http://www.endpcnoise.com/cgi-bin/e/std/sku=kaze_master"]
http://www.endpcnoise.com/cgi-bin/e/std/sku=kaze_master[/URL]

---

### Post by M4rotku on 2009-07-19
As far as I can tell, that's the only thing that could've happened.  I was using a program that I wrote to rip a bunch of tv episodes off of a dvd in a loop one after the other.  after about the 30th, the drive started failing.

Edit:  it can't be a separate hardware thing b/c I want to try and release this software, but I can't have it burning up ppl's drives.  I guess I'll just add a pause function.  How long should I pause between rips?  It's currently set for 10 minutes.

---

### Post by moster on 2009-07-19
I would go by feel. If you take out DVD and it feels very warm, then it is time for rest.

It depends what temperature you have in case and is drive single or you have one on top of another. I mean you have free space on top and bottom of the drive. Heat must go away somehow.

Worst case is that you have two drives, one on top of another and no FANs inside computer.

---

