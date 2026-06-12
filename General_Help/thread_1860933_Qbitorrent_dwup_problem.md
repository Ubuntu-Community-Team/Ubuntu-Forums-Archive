---
title: "Qbitorrent dw/up problem"
date: 2011-10-15
forum: General Help
---

### Post by sweetchuggagun on 2011-10-15
Hi there!

I'm on Ubuntu 11.04 but this happened to me on 10.04 and 10.10 as well. For torrent download I use qbitorrent v2.6.9 installed from the Software Center and in every new session qbitorrents checks the downloaded files from 0.0% and it usually remain stuck except when I add new files for download. When I download other files it starts rechecking the content of the files and starts seeding, but in the next session it takes it all over again. It's weird and annoying because I can't seed except the time I dw something else.

I mention that the destination folder for the incomplete and complete files from qbitorrent are on a NTFS partition(and I don't have Windows installed). 

Thanks in advance.

---

### Post by lovinglinux on 2011-10-15
Right-click on the torrent and select the option to force recheck. See if that helps. I suppose it could be some issue with the NTFS partition.

---

### Post by sweetchuggagun on 2011-10-15
Well only force rechecking helps, but just from time to time.

---

### Post by lovinglinux on 2011-10-15
> **sweetchuggagun said:**
> Well only force rechecking helps, but just from time to time.

Have you tried to save some torrents on a different partition, just to see if the problem can be reproduced?

---

### Post by sweetchuggagun on 2011-10-18
I think I found the problem. The qbitorrent gets stuck because my NTFS partition doesn't mount automatically at startup. I have to click on it before i start qbitorrent in order to work. :)

---

### Post by lovinglinux on 2011-10-18
I am glad you found the problem.

Please mark the thread as SOLVED using the Thread Tools menu.

---

