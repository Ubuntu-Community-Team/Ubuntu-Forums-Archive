---
title: "what's this drive?????????"
date: 2010-03-03
forum: General Help
---

### Post by flyingsliverfin on 2010-03-03
i only have 2 hdds in my dell... however, i somehow messed everything up. I wiped both hdd's, but now anything that tries to detect the hdd's thinks there are 3 hdds...
:confused:

the normal ones are:
/dev/sda1--- my windows  (before)
/dev/sdb1 --- my ubuntu (before)
the strange one is:
/dev/mapper/isw_cdedbgbdeb_ARRAY

it has the (almost) exact same properties:
first sector: 0
last sector: 156232124

/dev/sda1 is:
first sector: 0
last sector: 156248189


can any1 tell what this is???

---

### Post by flyingsliverfin on 2010-03-03
oh just found out its an RAID1 mirror array...

is there a way to get rid of it? its messing things up. i tried looking in the BIOS but couldn't find a choice "off"

---

