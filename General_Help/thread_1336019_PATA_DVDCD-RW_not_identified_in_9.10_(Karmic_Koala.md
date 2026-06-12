---
title: "PATA DVD/CD-RW not identified in 9.10 (Karmic Koala)"
date: 2009-11-24
forum: General Help
---

### Post by Gael33 on 2009-11-24
I went through this problem with Jaunty and never did solve the problem ... the problem being that the operating system does not recognize my PATA HP 1040d DVD/CD-RW. If there is anyone out there who has personally overcome this problem please let me know how you did it. I am not technically minded and my computer skills are rather modest compared with most of my peers on this site ... so please make it simple and step by step, (I can however follow instructions quite well).
Computer is a HP Compaq dx2250. (business machine)
Memory is 1.8 GB
75 GB hdd
AMD Athlon 64
System is Linux Ubuntu 9.10 32 bit (tried 64 bit ... same problem). 

thank you,
gael.

---

### Post by dcstar on 2009-11-25
> **Gael33 said:**
> I went through this problem with Jaunty and never did solve the problem ... the problem being that the operating system does not recognize my PATA HP 1040d DVD/CD-RW. If there is anyone out there who has personally overcome this problem please let me know how you did it. I am not technically minded and my computer skills are rather modest compared with most of my peers on this site ... so please make it simple and step by step, (I can however follow instructions quite well).
Computer is a HP Compaq dx2250. (business machine)
Memory is 1.8 GB
75 GB hdd
AMD Athlon 64
System is Linux Ubuntu 9.10 32 bit (tried 64 bit ... same problem). 

thank you,
gael.

Make sure the drive jumpers are set to Master (assuming it is the only device on the IDE channel).

---

### Post by Gael33 on 2009-11-25
> **dcstar said:**
> Make sure the drive jumpers are set to Master (assuming it is the only device on the IDE channel).

Firstly,thanks for replying.

As I said earlier, I am no techy but I follow instructions well. 
I have a DVD-ROM drive that is seen by the OS, but the DVD-RW is not seen. Would I be right in thinking that because they are connected to the Motherboard differently ... the DVD-ROM is on a gray strip cable and the DVD-RW is on a completely different cable which is black and round, both drives are therefore set to master on the jump settings? That would seem a little odd because both drives are identified and seen by WindowsXP and both work perfectly well, or is it a case of Ubuntu 9.10 functioning differently from WindowsXP that this problem has arisen?
I will check the jumper settings later today and post the result.

Thanks again,
gael.

---

### Post by jacobs444 on 2009-11-25
the jumper settings typically only relate to the ribbon connector (the 2 inch wide one) if drive is master then it should be on the last connector, if slave it should be on the first connector after the motherboard. Sata the thin connector typically does't need a jumper setting. You can also use the CS or cable select setting on pata, and the drive will be configured as to it's position on the cable.

---

### Post by Gael33 on 2009-11-25
> **Gael33 said:**
> Firstly,thanks for replying.

As I said earlier, I am no techy but I follow instructions well. 
I have a DVD-ROM drive that is seen by the OS, but the DVD-RW is not seen. Would I be right in thinking that because they are connected to the Motherboard differently ... the DVD-ROM is on a gray strip cable and the DVD-RW is on a completely different cable which is black and round, both drives are therefore set to master on the jump settings? That would seem a little odd because both drives are identified and seen by WindowsXP and both work perfectly well, or is it a case of Ubuntu 9.10 functioning differently from WindowsXP that this problem has arisen?
I will check the jumper settings later today and post the result.

Thanks again,
gael.

Hi again.
I had a look in the CMOS and it gave all the information there.
Here is what is written in the CMOS;
PATA Controller - Enabled.
PATA CH0 Master - None.
PATA CH0 Slave - HP DVD-Writer 1040d.

SATA Controller - Enabled.
SATA Mode - Legacy IDE.
SATA Ch1 Master - Samsung HD161HJ.
SATA CH1 Slave - None.
SATA CH2 Master - HL-DT-STDVD-ROM GDRH10N.
SATA CH2 Slave - None.

Question; What would happen if the jumpers were set to PATA CH0 Master or CS on the HP DVD-Writer 1040d unit?

Hope this information helps.

gael.

---

### Post by jacobs444 on 2009-11-25
then it usually wouldn't be recognized by either the Bios or the OS, but that isn't always the case, sometimes one or the other doesn't recognize, and other times just random errors. I am betting that the jumper is set to master, yet the drive is in the slave position, i.e. the second position on the cable. I am fallable  though.

---

### Post by Gael33 on 2009-11-25
> **jacobs444 said:**
> then it usually wouldn't be recognized by either the Bios or the OS, but that isn't always the case, sometimes one or the other doesn't recognize, and other times just random errors. I am betting that the jumper is set to master, yet the drive is in the slave position, i.e. the second position on the cable. I am fallable  though.

The DVD-Writer (PATA) is not on a ribbon connector, it is connected by a black round cable and I assume is therefore on a different system (if that's the right word) than the DVD-ROM which is (SATA).

gael.

---

### Post by jacobs444 on 2009-11-25
on the end of this cable is there a 2inch wide rectangle? maybe i am behind the times, but i have never seen around pata connector, still no matter what connector, if it is pata, it needs to have the jumper set as described above.

---

### Post by Gael33 on 2009-11-25
> **jacobs444 said:**
> on the end of this cable is there a 2inch wide rectangle? maybe i am behind the times, but i have never seen around pata connector, still no matter what connector, if it is pata, it needs to have the jumper set as described above.

You have confused me. The PATA DVD-Writer is the only thing on the cable. As to the shape of the cable I am only going off memory as I haven't looked inside my computer for several months ... there could very well be a 2" wide rectangle. Nether the less, as this devise is the only thing connected in this way, should the PATA DVD-Writer not be set as master or CS.
Please look at my CMOS settings in a previous post earlier today and I think you will understand what I am getting at. 

gael

---

### Post by dcstar on 2009-11-25
> **Gael33 said:**
> Hi again.
I had a look in the CMOS and it gave all the information there.
Here is what is written in the CMOS;
PATA Controller - Enabled.
PATA CH0 Master - **None.**
PATA CH0 Slave - **HP DVD-Writer 1040d**.
........

Make it Master.

---

### Post by egalvan on 2009-11-26
This wiki page has some good shots of the PATA style cable and connector.
Notice the large number of pins that the connector has.
the cable can either be a flat ribbon, or a "round" type.

[http://en.wikipedia.org/wiki/Parallel_ATA](http://en.wikipedia.org/wiki/Parallel_ATA)


The SATA style cable does not have as good shots...

[http://en.wikipedia.org/wiki/Serial_ATA](http://en.wikipedia.org/wiki/Serial_ATA)

---

