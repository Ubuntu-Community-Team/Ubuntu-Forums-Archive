---
title: "Boot lockup with ANY linux"
date: 2006-04-21
forum: General Help
---

### Post by menghuo on 2006-04-21
i'm attempting to reinstall windows, and finally go back to dual booting with linux after a year of not. unfortunately, the new computer i've gotten since then doesn't seem to like linux, or something. i've gone from one i built myself to a compaq, so i'm not surprised there's a little bit of a hiccup but i'm not sure what it is this time. (note: i've removed the compaq restore partition, and am running my own copy of XP. the only compaq-ness left on this computer is the bios)

anyhow, i've been attempting to boot ubuntu live, knoppix, etc. to see how various linux setups handle this computer's hardware, and they won't boot. i've tried everything from my disc-pile from old mandrake 8 discs to shiny new ubuntu 5.10 and none finish booting. they always stop partway, no hard drive activity, CD activity, no nothing. just silence.

this is a photo of where ubuntu stops and i'm quite sure it's referring to the one hard drive in the computer, but beyond that i'm lost
[http://img150.imageshack.us/my.php?image=10016920ic7rp.jpg](http://img150.imageshack.us/my.php?image=10016920ic7rp.jpg)

---

### Post by elamericano on 2006-04-21
Was that knoppix 5.0? My advice with brand new hardware would be to try the newest distro you can get your hands on. Knoppix 5 was just out in March, so I'd say that was your best bet. Hopefully Dapper will work for you. You can download the Beta Live CD here: [http://releases.ubuntu.com/6.06/](http://releases.ubuntu.com/6.06/)

---

### Post by menghuo on 2006-04-21
knoppix 4, but this computer's not too new. maybe ~8 months past "new"

---

### Post by PriceChild on 2006-04-21
I think that you should try booting with the option of
```
acpi=off
```
So for example when about to boot knoppix:
```
knoppix acpi=off
```
If this works, then we're getting somewhere :)

---

### Post by menghuo on 2006-04-21
tried it on the ubuntu livecd and it didn't work. didn't try knoppix, but they're both isolinux

also i noticed something odd

64bit ubuntu livecd boots to problem area
32bit ubuntu livecd forces a hard reset even when i run with no boot parameters, seconds after i hit enter

=( i want 32 more than 64, anyone know about that?

---

### Post by menghuo on 2006-04-22
i've tried a few more setups with no help

cd drives unplugged: same problem
one cd drive unplugged: same problem
soundcard on irq11 removed: same problem
sata hard drive unplugged: **five screens of text farther, then a lockup like before about something involving IRQs and SATA**


=( help?

---

### Post by Jason_25 on 2006-04-22
Have you ran a few passes of memtest86 on the pc?  Were your install CD's burned at the lowest possible speed?

---

### Post by menghuo on 2006-04-22
my CDs are the official factory-printed red/yellow ones

i don't know what memtest is, but for reference if it matters, i can run windows xp, 3DSmax, winamp, photoshop, illustrator and read data from both CD drives at the same time with no issues, so the system's in full working order, outside of not being able to boot any linux

---

### Post by Jason_25 on 2006-04-22
The "official" ubuntu discs have been known to still have problems.  Also, computers that are stable in windows have been known to crap out running linux.  It's tough on your ram.  I would suggest running memtest86 from the ubuntu install cd.

---

### Post by menghuo on 2006-04-23
PROGRESS!

okay went back and tried knoppix 4 again

i typed 

[knoppix noacpi acpi=off]

knoppix booted quickly and flawlessly and could access all devices

it also worked with

[knoppix noacpi acpi=off bios=pci]

however, the same parameters on ubuntu, 64 or 32, live or install, lead to the lockup in the original photo. no difference

P.S. memtest had no problems

---

### Post by menghuo on 2006-04-24
=( nobody has any idea?

---

### Post by Jason_25 on 2006-04-25
So did you reburn the ISO at the lowest speed possible?

---

### Post by Efwis on 2006-04-25
[QUOTE=menghuo]PROGRESS!

okay went back and tried knoppix 4 again

i typed 

[knoppix noacpi acpi=off]

knoppix booted quickly and flawlessly and could access all devices

it also worked with

[knoppix noacpi acpi=off bios=pci]

however, the same parameters on ubuntu, 64 or 32, live or install, lead to the lockup in the original photo. no difference

P.S. memtest had no problems[/QUOTE]
change it from 

```
distro noacpi acpi=off
```
to 
```
distro acpi=off
```

I'm thinking the dual command telling the system not to use acpi is conflicting the program and preventing proper boot up

---

### Post by menghuo on 2006-04-26
knoppix is happy with the dual command
ubuntu gets the same problem with one, the other or both. =(

---

### Post by cracker on 2006-04-26
I have a similar problem with my hp pavillion zv6000. The only linux distro I've gotten to boot on it is slackware, the rest lock up at various points, even with numerous combinations of commands. I think it is a specific issue with HP/Compaq Athlon 64 motherboards.

---

### Post by menghuo on 2006-04-28
>>I think it is a specific issue with HP/Compaq Athlon 64 motherboards.

i'll have to agree after much more trying

and i think the word issue isn't appropriate, as this is no doubt deliberate. my dell laptop (free, no i would never pay for a dell) gets the same error due to a deliberate anti-linux bios quirk, there's a fix out there i'm going to install, but unfortunately no fix for the HPs (which is what my desktop is, again regretting letting the parents send me off to college with a computer rather than money to throw my own together)

---

### Post by menghuo on 2006-06-10
bumping so someone new might see it, still hoping

---

### Post by foofightrs777 on 2006-06-10
Have you tried to install your video card drivers through command line?  I had an NVIDIA card before that simply HATED generic drivers.  It would immediately lock up X.

---

### Post by menghuo on 2006-06-12
i can't install anything, period, and it's locking up at something about drives, so i don't think that's the problem

i have an onboard ATI chip, also. not NVIDIA (i wish)

---

### Post by Joshatdot on 2006-06-13
Have you tried 6.06 LTS Dapper Drake yet?

and try these boot options: noapic nolapic

---

### Post by menghuo on 2006-06-13
[QUOTE=Joshatdot]Have you tried 6.06 LTS Dapper Drake yet?[/QUOTE]

nope

[QUOTE=Joshatdot]and try these boot options: noapic nolapic[/QUOTE]

will do

---

### Post by menghuo on 2006-06-15
[QUOTE=Joshatdot]Have you tried 6.06 LTS Dapper Drake yet?

and try these boot options: noapic nolapic[/QUOTE]

noapic nolapic takes me to this screen:
[[IMG]http://img108.imageshack.us/img108/1223/1001778large9ni.th.jpg[/IMG]](http://img108.imageshack.us/my.php?image=1001778large9ni.jpg)

if i do like it says and add pci=biosirq i end up on the same screen anyways

---

### Post by menghuo on 2006-06-21
nobody?

---

