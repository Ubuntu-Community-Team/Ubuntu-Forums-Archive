---
title: "Help with ddrescue"
date: 2010-09-08
forum: General Help
---

### Post by damnated on 2010-09-08
I'm trying to recover data from a formatted hdd, and tried ddrescue, but it turns out I'm not exactly sure how to use it. I've read the tutorial associated with it, but I screwed something up it seems, because after I typed ```
sudo ddrescue /dev/sdc /dev/sdb logfile
``` it started rescuing files, but after it finished the files were nowhere to be found, yet about 3 GB were missing from my system drive. This must be the rescued data, but I can't find it in /dev ... 

The formatted hdd was mounted at /dev/sdc and there was nothing at /dev/sdb .
Any ideas?

---

### Post by mips on 2010-09-18
> **damnated said:**
> I'm trying to recover data from a formatted hdd, and tried ddrescue, but it turns out I'm not exactly sure how to use it. I've read the tutorial associated with it, but I screwed something up it seems, because after I typed ```
sudo ddrescue /dev/sdc /dev/sdb logfile
``` it started rescuing files, but after it finished the files were nowhere to be found, yet about 3 GB were missing from my system drive. This must be the rescued data, but I can't find it in /dev ... 

The formatted hdd was mounted at /dev/sdc and there was nothing at /dev/sdb .
Any ideas?

ddrescue is not going to recover your files for you, it is used make exact duplicate images of working or failing drives. So the copied drive will look exactly like the formatted drive seeing they are duplicates.

You need to do data recovey which is more easily done from an image file with various tools.
[https://help.ubuntu.com/community/DataRecovery#Extract%20individual%20files%20from%20recovered%20image](https://help.ubuntu.com/community/DataRecovery#Extract%20individual%20files%20from%20recovered%20image)

---

