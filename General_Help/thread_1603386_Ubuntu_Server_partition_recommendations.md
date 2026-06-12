---
title: "Ubuntu Server partition recommendations"
date: 2010-10-22
forum: General Help
---

### Post by NJC on 2010-10-22
Didn't think this was too "Server" specific, so posted here:

I just purchased a shiny 1TB WD Blue drive as storage for my Ubuntu file server. I want to use to backup via SSH/rsync my dual-boot XP/Ubuntu 10.10 Desktop PC. 

I'll do either of the following:

1/ Add as 2nd drive to Server, and format/install LVM as one giant partition
2/ Replace Server drive with new 1TB and re-install Ubuntu Server. The data can easily be copied to Server so losing contents is fine. 

Any other recommendations for partitioning?

**EDIT: **I went with Option #2 and used LVM (logical volume manager) to partition the whole drive. This was the default option for my installation.

Only oddball thing is the low Timed cache reads:

Timing cached reads:   1102 MB in  2.00 seconds = 550.79 MB/sec
Timing buffered disk reads:  358 MB in  3.01 seconds = 118.88 MB/sec

---

