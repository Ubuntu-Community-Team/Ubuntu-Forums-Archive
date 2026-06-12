---
title: "computer dead. boot order problem?"
date: 2011-05-02
forum: General Help
---

### Post by 4042966262 on 2011-05-02
im having trouble. this is typed on the Wii. the Desktop Computer running Lubuntu is dead. on boot I get  
PXEE61 Media Test Failure-check cable
PXE-MPF Exiting PXE ROM
if a cable is unplugged..where? I WAS messing with hard drives.. weird thing is, on BIOS>Strorage>Boot Order it shows.
 Diskette Drive (A:) First
USB Device Second
Compaq Ethernet Controller Third (ps what on EARTH is that!?!)
so it looks like my hard drive is disconnected. thing is to my untrained eye, i see nothing wrong. any ideas guys?

---

### Post by 4042966262 on 2011-05-02
ps, its a Comppaq 5320 Us (5000 Series)

---

### Post by TeoBigusGeekus on 2011-05-02
If you changed the connection order of your drives, check out their jumpers.

The 3rd option you get is to boot via network (in small words).

---

### Post by K_45 on 2011-05-02
You must have activated an option to boot via LAN i.e. network controller. Boot into the BIOS and find an option to result everything to defaults. Then change everything back to the way it was when it was working. If that doesn't work you can clear the CMOS jumpers on your motherboard or remove the battery for a few mins and then restore working settings.

---

### Post by 73ckn797 on 2011-05-02
> **TeoBigusGeekus said:**
> If you changed the connection order of your drives, check out their jumpers.

This

---

### Post by 4042966262 on 2011-05-02
restore to deafults?  its not there. strange, it used to be.. battery is out im looking at it. and what on earth are jumpers???

---

### Post by K_45 on 2011-05-02
Jumpers are little bits of plastic you can set to determine the HDD boot order and some settings, see here:

[www.wdc.com/en/library/eide/2579-001037.pdf](www.wdc.com/en/library/eide/2579-001037.pdf)

---

### Post by 4042966262 on 2011-05-02
after putting the battery back in, pc BIOS shows only Diskette in boot options

---

### Post by TeoBigusGeekus on 2011-05-02
> **4042966262 said:**
> ...and what on earth are jumpers???

If you changed your drives from masters to slaves (or the opposites) you have to adjust the jumpers at their back.
[IMG]http://www.studynotes.net/images/seagate-jumpers.gif[/IMG]

---

### Post by 4042966262 on 2011-05-02
> **K_45 said:**
> Jumpers are little bits of plastic you can set to determine the HDD boot order and some settings, see here:

[www.wdc.com/en/library/eide/2579-001037.pdf](www.wdc.com/en/library/eide/2579-001037.pdf)link not working. im on a wii. and cannot open PDF

---

### Post by K_45 on 2011-05-02
Are you sure an option to restore defaults or something similar isn't there? What motherboard do you have?

---

### Post by 4042966262 on 2011-05-02
what do i want the pice of plastic to be set to?

---

### Post by 4042966262 on 2011-05-02
how do i tell what kind of motherboard i have?

---

### Post by K_45 on 2011-05-02
Type:

```
sudo lshw -html > results.html && firefox results.html &
```

Look through it, your motherboard is probably listed towards the top. 

For the jumpers, what are they currently set to?

---

### Post by 4042966262 on 2011-05-02
5 prongs, it was set to the second to the right. i set it on first and rebooted (after setting date and time) got same error. set it to the last and still got the error. hmm..

---

### Post by 4042966262 on 2011-05-02
where do i type that code? i can not open terminal that i know of

---

### Post by K_45 on 2011-05-02
> **4042966262 said:**
> 5 prongs, it was set to the second to the right. i set it on first and rebooted (after setting date and time) got same error. set it to the last and still got the error. hmm..

Set it back to defaults, or follow the earlier screenshot on page #1.

---

### Post by TeoBigusGeekus on 2011-05-02
Read [this]("http://www.pcguide.com/ref/hdd/if/ide/confJumpering-c.html").

---

### Post by 4042966262 on 2011-05-02
> **K_45 said:**
> Set it back to defaults, or follow the earlier screenshot on page #1.

i had set the slaves after i had pulled battery. so it should be reset it wanted time and date.

---

### Post by 4042966262 on 2011-05-02
> **TeoBigusGeekus said:**
> Read [this]("http://www.pcguide.com/ref/hdd/if/ide/confJumpering-c.html").

that was a looooot to read

---

### Post by 4042966262 on 2011-05-02
guys, i disconnected a lot of wires in computer, and started it and got the same error. i think its a wire in the wrong place. can somone show me where the wires go? im pretty sure this is my problem. after all the computer worked fine before i started looking at its hard drive.

---

### Post by K_45 on 2011-05-02
What wires? Do you mean the SATA cables, front panel, IDE, -?

---

### Post by 4042966262 on 2011-05-02
cables in the computer. hard drive cables, cd drive cables, floppy disk cables.. left them pluggen in the motherboard though

---

### Post by 73ckn797 on 2011-05-03
> **4042966262 said:**
> cables in the computer. hard drive cables, cd drive cables, floppy disk cables.. left them pluggen in the motherboard though

Parallel (PATA) hard drives use a 41 pin plug. Two are typically near each other at one end and the other end is plugged into the MB. The first end plug is for the Master drive and the second one almost next to the end is for a slave drive.

Serial (SATA) drives have a power cable and data cable that are fairly straight forward. SATA 1 on the MB would be to either a hard drive or CD/DVD drive that accepts that type of connector. If there are several SATA drives then boot options/order can be set in BIOS or on boot up by pressing F9/F10 or F12. It depends on the BIOS.

The Floppy drive (I assume you mean the 3.5" plastic disk drive) is a smaller (fewer pins) than the hard drive 41 pin connector and will only fit a floppy drive. Typically there is a separate connector on the MB for that.

---

