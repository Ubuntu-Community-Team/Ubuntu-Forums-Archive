---
title: "Weird (?) Boot Problem"
date: 2006-01-27
forum: General Help
---

### Post by jacko69 on 2006-01-27
Hi all,

Am a bit of a newbie .. in particular to Linux .. but have got things installed and working with relatively no problems - well kinda except one.

The system takes about an hour (yep) to from when the boot command executes until the GUI "booting" screen appears. Once the GUI's up it takes one or two minutes which appears to be the standardish time from what I can see here in the forums. 

Whilst it's reasonably old hardware, it shouldn't be that old - as a contrast it takes Knoppix about 2 mins to load fully. 

The only thing that my limited knowledge has dropped into my head is that it could be related to the BIOS settings - that when powersave or something tries to kick in (60 mins) then it actually starts loading properly .. but then again I could just be making that up!

If anyone has suggestions on things that may be worth checking please throw them at me .. figuratively.

Thanks,
Jacko

---

### Post by dcstar on 2006-01-28
[QUOTE=jacko69]Hi all,

Am a bit of a newbie .. in particular to Linux .. but have got things installed and working with relatively no problems - well kinda except one.

The system takes about an hour (yep) to from when the boot command executes until the GUI "booting" screen appears. Once the GUI's up it takes one or two minutes which appears to be the standardish time from what I can see here in the forums.
......
If anyone has suggestions on things that may be worth checking please throw them at me .. figuratively.

Thanks,
Jacko[/QUOTE]
Edit /etc/default/bootlogd to read (and ignore any error message on bootup):

BOOTLOGD_ENABLE=Yes

Edit /etc/default/rcS to have:

VERBOSE=yes

You then need to press CTRL-ALT-F1 when the boot process stalls to see the text screen, this should give you some idea as to where it is stalling.

More information can be gleaned by the various var/log files, it could be something as simple as misconfigured DNS setting (or IPv6) slowing things down.

---

