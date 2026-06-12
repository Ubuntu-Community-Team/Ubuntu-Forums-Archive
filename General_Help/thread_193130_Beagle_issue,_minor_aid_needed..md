---
title: "Beagle issue, minor aid needed."
date: 2006-06-09
forum: General Help
---

### Post by turbojugend_gr on 2006-06-09
Well as a user of Dapper, I have beagle in my system. The thing is that I don't like the fact that is the default ubuntu search app, this is due to the fact that I am under the impression that I need to enable extended attributes or something to get it to show me some results.. (I am only getting results when it comes to search something like anjuta and the anjuta IDE starter comes up, only nothing else, not even the .anjuta folder in my home!)

I believe the problem originates to the lack of extended attributes for my disks, I may be wrong but please help me. Should I enable them (any SAFE way to do so?) or is it something else ? Please any help is welcomed. Thank you all again, and again...

PS: Beagle daemon (beagled) is set to run on start up as it should.

---

### Post by mclaren_fan on 2006-06-09
I had the same problem.
Just add user_xattr after defaults in /etc/fstab like this:
/dev/mapper/VolGroup00-LogVol02 /home           ext3    defaults,user_xattr
If it still doesn't work then try to reinstall beagle, that's what i did to get it working.

---

### Post by turbojugend_gr on 2006-06-11
Well before doing anything I would like to point some questions,

first of all I have 4 major partitions I would like to search with beagle: 
ext3 (/), ext3 (/home), fat32 (/winux -windows/linux used space), ntfs (/winxp -not actually importatant to search in it).

Well is it safe to enable user_xattr (extended attributes) for fat32 and ntfs?

If this is the only cause to beagle misbehaviour: 1. How come fstab hasn't xattr by default in ubuntu?         2. How come searches don't even return my evolution contacts results?

Plz any help is appreciated!

---

