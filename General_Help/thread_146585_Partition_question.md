---
title: "Partition question"
date: 2006-03-18
forum: General Help
---

### Post by m00nd0g on 2006-03-18
Does anyone know for sure as to how many partition can be created on a 100gb hard drive ? I am referring about just to use all the so many different types of linux OS only ?

TIA

---

### Post by powder on 2006-03-18
You can create a maximum of four primary partitions and as many logical partitions as you want within a primary partition.

---

### Post by Lunixfanboy on 2006-03-18
Assuming you are using an IDE drive, the drive can have a maximum of 4 primary partitions, or 3 primary partitions and 1 extended partition, which will be able to hold 21 logical partitions (the 21 maximum dates from the OLDEN days of Windows hard-coding drive letters to partitions, C going to /dev/hda1 and so on out to Z).

---

### Post by m00nd0g on 2006-03-18
So lets see if i have this right , With my 100gb ide hard drive , I can slice it up 4 ways ( 4 x 25 )  and on each partition I can have 21 logical partitions ? Is this correct ? 

TIA

---

### Post by powder on 2006-03-18
Not completely sure but I think you can create more than 21 logicals these days.

---

### Post by Ramses de Norre on 2006-03-18
But who needs such an amount of little partitions? :-k

---

### Post by powder on 2006-03-18
[QUOTE=Ramses de Norre]But who needs such an amount of little partitions? :-k[/QUOTE]

And why do they want to punish themselves? :mrgreen:

---

### Post by m00nd0g on 2006-03-18
[QUOTE=Ramses de Norre]But who needs such an amount of little partitions? :-k[/QUOTE]

Its only going to be to  experiment , I have like about 10 HHD which I use on 3 comps , I want to try one of them hdd just for linux OS only and install as many OS I can just to see which ones that I would like ...

[www.distrowatch.com](www.distrowatch.com) From here I can try them out , Mind you I do have to choose the correct ones thats are for my unit

---

### Post by infoseeker on 2006-03-19
Your GRUB menu.lst file in would be interesting to see (and a pain to maintain) !!! :D

---

### Post by Lunixfanboy on 2006-03-19
[QUOTE=m00nd0g]So lets see if i have this right , With my 100gb ide hard drive , I can slice it up 4 ways ( 4 x 25 )  and on each partition I can have 21 logical partitions ? Is this correct ? TIA[/QUOTE]Nope. Each primary partition is just that, a PRIMARY partition. The logical partitions are created in an extended partition, of which you can have one, so 3 primaries and 21 logicals in the extended gives you 24 (since A: and B: are reserved for floppies, you have C: through Z: available).

---

### Post by Ramses de Norre on 2006-03-19
Why does linux have the same retrictions on logical partitions? Are there more reasons then the limitations of the drive letters in win?

---

### Post by Lunixfanboy on 2006-03-19
[QUOTE=Ramses de Norre]Why does linux have the same retrictions on logical partitions? Are there more reasons then the limitations of the drive letters in win?[/QUOTE]By way of clarification/partial retraction of my previous statements concerning logical partitions in a Linux file system:
"One primary partition of a hard drive may be subpartitioned. These are logical partitions. This effectively allows us to skirt the historical four partition limitation.

The primary partition used to house the logical partitions is called an extended partition and it has its own file system type (0x05). Unlike primary partitions, logical partitions must be contiguous. Each logical partition contains a pointer to the next logical partition, which implies that the number of logical partitions is unlimited. However, linux imposes limits on the total number of any type of prtition on a drive, so this effectively limits the number of logical partitions. This is at most 15 partitions total on an SCSI disk and 63 total on an IDE disk." ([http://www.faqs.org/docs/Linux-mini/Partition.html](http://www.faqs.org/docs/Linux-mini/Partition.html))

---

