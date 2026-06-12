---
title: "Can i mix RAID 0 and RAID 5 on the same drives?"
date: 2011-12-30
forum: General Help
---

### Post by geekyhawkes on 2011-12-30
Im thinking of reinstalling my ubuntu machine and was planning on making "better" use of the drives I have hanging around.

I have a 40gb SATA drive, 2x250GB SATA drives and one 500gb drive. 

I use the 500 gb drive to backup my PS3 films/games etc so was planning on leaving that out of the equasion (unless someone can convince me otherwise).

I was thinking of doing the following:

40gb drive SDA:

SDA 1:  1gb Boot for grub2
SDA 2:  3gb Swap
SDA 3:  30gb (ish) /DATA in RAID 5
SDA 4:  6gb non RAID data

250gb drive SDB:

SDB1:   30gb (ish) /DATA in RAID 5
SDB2:   220gb Xubuntu install in RAID 0

250gb drive SDC as above.

Im not sure if this set up will work as i want really.  What im trying to get at is that my data is fast and mirrored (hence RAID5) but the OS itself has speed available in RAID0 (not too bothered about the mirroring here). 

Clearly the ideal would be to just go and buy another 250gb drive and RAID 5 all the volumes but im trying to make best use of what i have hanging around.

Thanks for any help, all suggestions welcome.

---

