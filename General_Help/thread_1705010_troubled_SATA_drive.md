---
title: "troubled SATA drive"
date: 2011-03-11
forum: General Help
---

### Post by chkneater on 2011-03-11
Now I know there have been some issues regarding SATA and IDE compatibility, but I don't think I fit in any of these issues.

Background: Karmic 2.6.31-23 generic, AMD Athlon3800+ 64 2400MHz
nvidia MCP51 Serial ATA Cont (rev1)

Two IDE HD: Seagate ST340014A and Maxtor 6B300R0

Came across WD200JS with damage to the pins.  The SATA pins were intact and undamaged, but the larger pinset next door was mangled.  I was able to untangle the pins so that none were touching.  Other than the pins the drive looks fine.

With IDE drives and SATA enabled in BIOS, gparted shows no SATA drives. Further more, totally disconnected  the IDE and disabled them in BIOS leaving ONLY SATA available and used the LIVE CD (9.04) and partition editor sees no drives.

The obvious conclusion at this point is the drive is Effed, HOWEVER I noticed on the Master drive (set drives as cable select) that to use non-IDE devices an extra pin is needed on the master drive, which I don't have an extra pin to test this.

These are my options: Drive is busted (I don't think it is, I felt it running with the liveCD); BIOS needs updating; or HOPEFULLY I just need an extra jumper pin.

I'm thinking the BIOS needs updating, who has any advice?
BTW: Compaq Presario SR2030NX

---

### Post by AlphaLexman on 2011-03-11
Is your Seagate drive a **7200.11**?
If yes, see: [Bricked Seagate hdd]("http://www.msfn.org/board/topic/128807-the-solution-for-seagate-720011-hdds/")

This happened to me :(

---

### Post by chkneater on 2011-03-11
Would that number be located on the drive or is it the model number?  I'm asking cuz it's in use an Idon't wanna take it out!  Thats what she said.

Now I understand the question, the Seagate drive is fine, it's the Western Digital that has been Tina Turner'd

---

### Post by AlphaLexman on 2011-03-11
> **chkneater said:**
> Would that number be located on the drive or is it the model number?I think they call it (7200.11) a **product number**, with many different **model numbers** (ST340014A).

Good luck though!

---

