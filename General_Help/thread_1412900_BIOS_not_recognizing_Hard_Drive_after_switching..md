---
title: "BIOS not recognizing Hard Drive after switching."
date: 2010-02-21
forum: General Help
---

### Post by gymophett on 2010-02-21
I switched the Hard Drive in my main desktop yesterday with another just so I could install something on it. Then, when I switched my other desktop hard drive back to it's original, it wouldn't detect it.

The power cables and all the connections are still good, because it still recognizes my other computers hard drive. 
I'm in deep trouble for screwing up the family PC, how can I fix it?

---

### Post by northrup on 2010-02-21
Try it the other way around: try booting the family computer's hard drive in another computer.  Is it detected?

Also, make sure that the IDE cable (if that's how you're connecting it to the motherboard) isn't backwards.  Likewise, make sure it's plugged into the same port as it was before (this applies to both SATA and IDE).

---

### Post by gymophett on 2010-02-21
> **northrup said:**
> Try it the other way around: try booting the family computer's hard drive in another computer.  Is it detected?

Also, make sure that the IDE cable (if that's how you're connecting it to the motherboard) isn't backwards.  Likewise, make sure it's plugged into the same port as it was before (this applies to both SATA and IDE).

It works in the other desktop.
Maybe I am plugging it in the wrong ports.. I highly doubt it though. I'm pretty sure it's right.
Should I take a picture and show you?

---

### Post by northrup on 2010-02-21
Sure, if you don't mind :)

---

### Post by gymophett on 2010-02-21
> **northrup said:**
> Sure, if you don't mind :)

I tried taking them, but you can't really tell what's going on in any of them. Soo that would make them pointless. :(
I'm about 99% sure they are plugged in right though.

---

### Post by northrup on 2010-02-21
Did you have to change any BIOS settings to get the other drive to work?

Also, just to clarify, is this an IDE or SATA drive?

---

### Post by gymophett on 2010-02-22
> **northrup said:**
> Did you have to change any BIOS settings to get the other drive to work?

Also, just to clarify, is this an IDE or SATA drive?

I believe it is IDE.
And I didn't alter any BIOS settings.
This is an odd situation indeed.

---

### Post by Mark Phelps on 2010-02-22
> **gymophett said:**
> I believe it is IDE.

Check the drive jumpers. If you're using one IDE drive cable, you must either have (1) one drive as Master and the other as Slave, or (2) both drives set to Cable Select.

---

### Post by tom.swartz07 on 2010-02-22
> **Mark Phelps said:**
> Check the drive jumpers. If you're using one IDE drive cable, you must either have (1) one drive as Master and the other as Slave, or (2) both drives set to Cable Select.
+1

also, if that doesnt work, try updating the BIOS for the computer- I had some problems similar to your case a few months ago until I realized i was 6 versions behind with BIOS updates. :rolleyes:

---

### Post by oldfred on 2010-02-22
If you are using cable select you must have the new 80 wire cable, not the old 40 wire. The 80 wire has three color connectors where the old one's were all one color.

[http://www.pcguide.com/ref/hdd/if/ide/confCable80-c.html](http://www.pcguide.com/ref/hdd/if/ide/confCable80-c.html)

---

