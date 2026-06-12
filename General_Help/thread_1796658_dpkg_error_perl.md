---
title: "dpkg error perl"
date: 2011-07-04
forum: General Help
---

### Post by megnetz on 2011-07-04
sudo dpkg -l | grep -v ^ii

+++-=====================================-===============================================-============================================
iFR linux-image-2.6.32-24-generic         2.6.32-24.41                                    Linux kernel image for version 2.6.32 on x86
iF  man-db                                2.5.7-2                                         on-line manual pager
iF  perl                                  5.10.1-8ubuntu2                                 Larry Wall's Practical Extraction and Report
iF  tzdata                                2011g-0ubuntu0.10.04                            time zone and daylight-saving time data
iU  tzdata-java                           2011g-0ubuntu0.10.04                            time zone and daylight-saving time data for 

So something is wrong with the linux kernel, perl, the manual and some random time zone programs. Any ideas?

---

### Post by megnetz on 2011-07-05
bump

---

### Post by megnetz on 2011-07-05
I just downloaded and installed the perl packages using dpkg, then the Update manager took care of the rest.

---

