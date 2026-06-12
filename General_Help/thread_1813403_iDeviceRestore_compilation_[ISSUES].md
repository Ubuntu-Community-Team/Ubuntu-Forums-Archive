---
title: "iDeviceRestore compilation [ISSUES]"
date: 2011-07-27
forum: General Help
---

### Post by aYunGDeviL on 2011-07-27
Hi guys, im in the process of compiling iDeviceRestore
Specs: Ubuntu 11.04
           Windows Vista
           Virtual Box

im stuck on the [ make linux && sudo make install ] for libirecovery
 i get the error saying [ make *** No rule to make 'linux' . Stop.

help me asap, i would really appreciate it..

---

### Post by aYunGDeviL on 2011-07-28
I wish someone actually had a WORKING TUTORIAL, smfh.

---

### Post by ubunt me on 2011-09-03
hey I was in the same state a few seconds ago. Carry out the following commands(without Quotes)
"cd ~"
"rm -rf libirecovery"
"git clone https://github.com/tokm/libirecovery.git"
"cd libirecovery"
"make linux && sudo make install"

It'll do fine! Just did it...........Don't follow tutorial from iFans because its full of spelling mistakes.

Suggestion: While doing "git clone http://git.sukimash*ta.com/libimobiledevice.git"

Do this instead:
"git clone git://git.sukimashita.com/libimobiledevice.git"

---

