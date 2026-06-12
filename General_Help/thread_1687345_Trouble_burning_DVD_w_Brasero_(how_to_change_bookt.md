---
title: "Trouble burning DVD w/ Brasero (how to change booktype?)"
date: 2011-02-13
forum: General Help
---

### Post by cero.kewl8080 on 2011-02-13
I've been trying to burn a backup copy of my Honda Navigation Map Data DVD-ROM, just in case the original disc gets damaged (it cost me $200 for the 2010 version).

I created the .iso which worked fine and appeared to include all the data files upon inspection of the new disc's contents.  When I burned the .iso onto a DVD +R DL disc, I received an error from my car's NAV system (i.e. "error reading disc.  Wrong disc format.).  

I searched a few forums, and located some info on changing the book type (a 4-bit value which identifies the disc format; located at beginning of the disc) from the DVD+R to DVD-ROM.  Apparently this makes the standalone disc player (ie. in this case my Honda NAV DVD-ROM player)  believe that it's reading a correctly formated disc.  I'm using a Lite ON 24X DVD RW SATA which, I've been led to believe from a hardware review article, does support book type management.

In this Ubuntu forum, on a separate thread, I found the following command which the user claims to have successfully changed the book type of a DVD +R DL disc to DVD-ROM:

```

sudo dvd+rw-booktype -dvd-rom -unit+r /dev/dvd

```

I received the following output 

```
 
:-[ LG_FCh failed with SK=5h/INVALID COMMAND OPERATION CODE]: No such device

```

I thought maybe I was referencing the wrong device name, so I checked system->administration->disk utility, which displayed, "device /dev/sr0" for this optical drive, so I changed the command to:

```

sudo dvd+rw-booktype -dvd-rom -unit+r /dev/sr0

```and received the same output:

```

:-[ LG_FCh failed with SK=5h/INVALID COMMAND OPERATION CODE]: No such device

```

QUESTION:  how do I change the book type of this device?
:confused::confused:

---

### Post by ajgreeny on 2011-02-13
Having made an .iso file of the contents of the original DVD, perhaps you should have burned the new one as a disk-image, not a data disk.  That would have given you a more or less exact copy of the original.  You could also have tried the **Copy CD/DVD **from the brasero start screen.

Apologies if that is what you did, but you did not say so in your post.

---

