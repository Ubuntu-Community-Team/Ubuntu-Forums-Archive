---
title: "Pata / sata?"
date: 2010-08-01
forum: General Help
---

### Post by ODECiF on 2010-08-01
I have purchased a 1TB SATA HDD and mistakenly connected it into a PATA-connector on my motherboard. I do have a SATA-connector on the board, but I didn't notice until now.

I have about 120GB of data on the hard drive, and now I wonder:
Can I just swap the port (from the PATA to the SATA) and still have all my data on the hard drive? Or do I need to back it all up and reformat it?

Best regards

Bob

---

### Post by CharlesA on 2010-08-01
How do you connect a SATA drive to a PATA connector? Did you use a SATA/PATA bridge?

---

### Post by ODECiF on 2010-08-01
To be honest, I think I installed it to the SATA-connector, but Ubuntu's telling me that it isnt :S
[IMG]http://minigris.net/~bobniel/privat/pata.png[/IMG]

I may be slightly blint at this moment, but doesn't it say "PATA Host Adapter"?

---

### Post by CharlesA on 2010-08-01
Best way to know for sure is to open the case and check tbh.

---

### Post by ODECiF on 2010-08-01
> **CharlesA said:**
> Best way to know for sure is to open the case and check tbh.

tbh?

---

### Post by jerenept on 2010-08-01
> **ODECiF said:**
> tbh?

To Be Honest

---

### Post by ODECiF on 2010-08-01
Oh..


Edit: Let me get this straight: SATA has the small cable that looks like an "L" at the ends, and PATA has the broad gray cable with about 41 pins at the ends?

---

### Post by CharlesA on 2010-08-01
> **ODECiF said:**
> Oh..


Edit: Let me get this straight: SATA has the small cable that looks like an "L" at the ends, and PATA has the broad gray cable with about 41 pins at the ends?
Correct.

There is no way to plug in a SATA drive to a PATA connector unless you use a bridge.
[IMG]http://www.cooldrives.com/ep.yimg.com/ca/I/cooldrives_2074_37198.jpg[/IMG]

---

### Post by ODECiF on 2010-08-01
Okay, well then I am sure that both of the disks seen above are connected by SATA. But then again, what about the "PATA Host Adapter" thingy? Are those 4 ports specifically for PATA->SATA converters or what?

Edit: Ment 2 ports obviously...

---

### Post by CharlesA on 2010-08-01
SATA is SATA, there is no SATA -> PATA on motherboards.

---

### Post by Lucky. on 2010-08-01
Disk Manager reports the same thing on my PC and I definitely have two SATA hard drives.  However in the BIOS, they're set to emulate IDE.

---

### Post by ODECiF on 2010-08-01
I know, was just thinking that they maybe they are made for the bridges you metioned before. I know it's a longshot, but I simply cannot find any other reason for them to be called they way they are called...

---

### Post by CharlesA on 2010-08-01
> **Lucky. said:**
> Disk Manager reports the same thing on my PC and I definitely have two SATA hard drives.  However in the BIOS, they're set to emulate IDE.

It's probably due to this. ^

---

### Post by ODECiF on 2010-08-01
> **Lucky. said:**
> Disk Manager reports the same thing on my PC and I definitely have two SATA hard drives.  However in the BIOS, they're set to emulate IDE.

Oh, that moght be it... But if you change them to work as regular SATA's, would that affect anything?

---

### Post by Lucky. on 2010-08-02
I keep mine in IDE mode at the moment because I use a soft RAID.

I've had to bounce between IDE and AHCI a few times with the past few Ubuntu releases.  9.04 and earlier wouldn't detect the RAID correctly, so I had to use IDE mode with the alternate installer and build a RAID manually.  In 9.10 I was able to run it in AHCI mode and Ubuntu would detect the RAID just fine and roll with it.  With 10.04 it was back to IDE.

If you're not using a RAID, it will probably work just fine either way (keeps fingers crossed).

---

### Post by ODECiF on 2010-08-02
Hmm, checked how my SATA's are configured and they are configured as "Enhanced" and "IDE", but I can only choose eighter "Enhanced", "Compatible" or something else (didn't sound like any regular SATA config anyway). And if you chose "Enhanced" or "Compatible" you could thereafter choose between "IDE", "RAID" or "AHCI" (or something like that..), and when I chose AHCI the drivers couldn't be located :/


... any tips or experiences are very much appreciated.

---

### Post by CharlesA on 2010-08-02
After you choose ACHI, the drives can't be found?

Just leave it as IDE then, I don't know what version of Ubuntu you are using but changing it from IDE to ACHI might have changed the way the drives were seen.

---

### Post by ODECiF on 2010-08-06
I believe the same... Oh well, no harm has bee dealt :o)

---

### Post by WiseHacker on 2011-02-22
I there, and sorry for digging up an old thread.

I found myself in the same situation - I have a IDE and a SATA drive connected to my Gigabyte G41M-Combo mother board yet Unbuntu only see all devices as PATA devices.

In the BIOS settings, my options are Auto, Combined and Enhanced - from what I can gather, Enhanced is meant to treat SATA as SATA and IDE as PATA, but this is not being reflected in Maverick.

The machine works, but but what is the point of having a SATA drive that runs at IDE speed because of the PATA interface>

---

