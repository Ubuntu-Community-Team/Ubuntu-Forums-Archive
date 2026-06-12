---
title: "How to upgrade Homebank"
date: 2011-07-29
forum: General Help
---

### Post by Oldhacker on 2011-07-29
For some time, I have been using Homebank happily. However, there are some features and improvements in the most recent edition that would be nice to have. The Ubuntu repositories are several editions behind with binaries.

It has been a while since I have done this, but as I remember I should:

1. Save the homebank data file.
2. Apt-get delete the current homebank
3. Download the latest homebank-4.4.tar.gz 
4. Then, ???

Please refresh my memory as to what to do next.

---

### Post by Oldhacker on 2011-07-30
I downloaded the .tar.bz unzipped and went through the usual compiling routine. It gave me an error message when attempting to open Homebank that it didn't have correct permission to open the last used file. Finally, I used Synaptic to uninstall and then re-installed with Synaptic. The "about" showed the version number to be the old version. However, I just did a dpkg -p to display what version that it is and it showed the new 4.1.1!!!
Then, I opened Homebank again and "about" showed it to be the new version. Yet another mystery solved.

---

