---
title: "PLZ HELP: recover RAID10 disks with Ubuntu dmraid."
date: 2010-03-22
forum: General Help
---

### Post by spamrefuse on 2010-03-22
Hi,
 
I hope somebody can help me through this terrible process of uncertainty.

My RAID10 (four 1TB harddisks) is broken.
The system can't boot anymore, as the OS is on the RAID.
One or even two disks in the RAID have trouble.....

I boot the system into UBUNTU 9.1 from USB stick, to hopefully be able
to acces the data on the RAID disks and copy it elsewhere:

-----------------------------
ubuntu@ubuntu:/sbin$ sudo dmraid -rvdddd
DEBUG: isw trying hard coded -2115 offset.
DEBUG: not isw at -523576832
DEBUG: isw trying hard coded -2115 offset.
DEBUG: not isw at -523576832
DEBUG: isw metadata found at -522494976 from probe at 232

DEBUG: isw metadata found at -522494976 from probe at 232

INFO: RAID devices discovered:

/dev/sdb: isw, "isw_eadbhddafc", GROUP, ok, 1953525166 sectors, data@ 0
/dev/sda: isw, "isw_eadbhddafc", GROUP, ok, 1953525166 sectors, data@ 0
-----------------------------

It seems to locate only two of the four disks, right? As a single RAID0 ?

What would be my next step to recover the data on this RAID?

Thank you!

Rob.

PS: here is more info by another dmraid command

ubuntu@ubuntu:/sbin$ sudo dmraid -s  -s -vdd
DEBUG: isw trying hard coded -2115 offset.
DEBUG: not isw at -523576832
DEBUG: isw trying hard coded -2115 offset.
DEBUG: not isw at -523576832
DEBUG: isw metadata found at -522494976 from probe at 232

DEBUG: isw metadata found at -522494976 from probe at 232

DEBUG: _find_set: searching isw_eadbhddafc
DEBUG: _find_set: not found isw_eadbhddafc
DEBUG: _find_set: searching isw_eadbhddafc_Volume0
DEBUG: _find_set: searching isw_eadbhddafc_Volume0
DEBUG: _find_set: not found isw_eadbhddafc_Volume0
DEBUG: _find_set: not found isw_eadbhddafc_Volume0
DEBUG: _find_set: searching isw_eadbhddafc_Volume0-0
DEBUG: _find_set: searching isw_eadbhddafc_Volume0-0
DEBUG: _find_set: searching isw_eadbhddafc_Volume0-0
DEBUG: _find_set: not found isw_eadbhddafc_Volume0-0
DEBUG: _find_set: not found isw_eadbhddafc_Volume0-0
DEBUG: _find_set: not found isw_eadbhddafc_Volume0-0
DEBUG: _find_set: searching isw_eadbhddafc
DEBUG: _find_set: found isw_eadbhddafc
DEBUG: _find_set: searching isw_eadbhddafc_Volume0
DEBUG: _find_set: searching isw_eadbhddafc_Volume0
DEBUG: _find_set: found isw_eadbhddafc_Volume0
DEBUG: _find_set: found isw_eadbhddafc_Volume0
DEBUG: _find_set: searching isw_eadbhddafc_Volume0-0
DEBUG: _find_set: searching isw_eadbhddafc_Volume0-0
DEBUG: _find_set: searching isw_eadbhddafc_Volume0-0
DEBUG: _find_set: found isw_eadbhddafc_Volume0-0
DEBUG: _find_set: found isw_eadbhddafc_Volume0-0
DEBUG: _find_set: found isw_eadbhddafc_Volume0-0
DEBUG: checking isw device "/dev/sda"
DEBUG: checking isw device "/dev/sdb"
DEBUG: set status of set "isw_eadbhddafc_Volume0-0" to 16
DEBUG: set status of set "isw_eadbhddafc_Volume0" to 16
*** Group superset isw_eadbhddafc
--> Active Superset
name   : isw_eadbhddafc_Volume0
size   : 1953519872
stride : 128
type   : raid01
status : ok
subsets: 1
devs   : 2
spares : 0
--> Active Subset
name   : isw_eadbhddafc_Volume0-0
size   : 1953519872
stride : 128
type   : mirror
status : ok
subsets: 0
devs   : 2
spares : 0
DEBUG: freeing devices of RAID set "isw_eadbhddafc_Volume0-0"
DEBUG: freeing device "isw_eadbhddafc_Volume0-0", path "/dev/sda"
DEBUG: freeing device "isw_eadbhddafc_Volume0-0", path "/dev/sdb"
DEBUG: freeing devices of RAID set "isw_eadbhddafc_Volume0"
DEBUG: freeing devices of RAID set "isw_eadbhddafc"
DEBUG: freeing device "isw_eadbhddafc", path "/dev/sda"
DEBUG: freeing device "isw_eadbhddafc", path "/dev/sdb"

---

