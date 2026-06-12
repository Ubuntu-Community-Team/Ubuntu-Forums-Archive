---
title: "can I mix SATA &amp; IDE with sortware raid?"
date: 2006-06-19
forum: General Help
---

### Post by beerorkid on 2006-06-19
messed around with trying to set up software raid while doing the manual partitioning with the text install of dapper.

I have a hodge podge of drives in the box and am trying to set up a network storage (samba)

- 40gb main OS IDE
- 300gb set it up for 200gb raid k SATA
- 250gb set it up for 200gb raid k SATA
- 200gb set it up for 200gb raid k IDE
- 250gb set it up for 200gb raid k IDE

all extra room has been left as free space and not partitioned, figure it will not be useable, not worried.  Wanting to get 600gb share out of it in raid 5.

having a few issues getting it to boot off the 40gb main OS drive, and figure it has something to do with how the drives are recognized in the BIOS.

couple questions though:

1. can I mix SATA and IDE in software raid?
2. should I wait till I have ubuntu up and running and do software raid after, or is setting it up during install better?
3. would it be easier with the live CD?
4. why is ubuntu sooooooo fricking cool? ;)

I might try out [freenas](http://www.freenas.org/index.php?option=com_frontpage&Itemid=1), but I would like to have ubuntu running on it as well so it can perform other duties.

srry I know there are a bunch of raid threads already, just could not find answers.

---

### Post by unf on 2006-06-19
Havent try, but Just Bunch Of Disks = JBOD ?

---

### Post by JoWilly on 2006-06-19
Yes you can. You can mix any kind of partitions (sata, ide, scsi,...).

Best is to set it up with the alternate install CD (you cannot do it with the liveCD). Don't forget that if you put your root partition on a software raid, you will need a separate boot partition (just put boot (min 100 Mb) at the beginning of one disk). And make all the partitions that will be part of the same raid the same size.

If you put the root partition in raid0 on the 5 disks it will be pretty darn fast :D

---

### Post by beerorkid on 2006-06-19
thanks for the reply.  i am currently installing with a 600GB raid 5 /share

I figured out my problem.  I had my primary and secondary IDE cables switched around.  i thought everything was right, so I thought mixing them might be the prob.  as always it was something so simple that hosed me.

I did try the live and saw it does not offer it.

I did get to mess arounf with freenas, but it did not like the cables being switched either.

hanging head in shame, but happy I learned a bunch ;)

---

### Post by Bokonon on 2006-06-19
Does this affect the compiz repos?  :p

---

