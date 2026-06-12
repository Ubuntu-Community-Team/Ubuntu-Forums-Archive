---
title: "Alternating two instances of the same program in launcher"
date: 2012-05-26
forum: General Help
---

### Post by pensadorlouco on 2012-05-26
I've recentlly upgraded from 11.10 to 12.04, and I've noticed a difference: before the upgrade (as an example), if I had two instances of Firefox (or any other software) minimized in the Unity launcher, I could just click-and-hold the cursor on Firefox's and the two instances would appear simultanealy for me to choose one.

But since I've upgraded to 12.04, I can't do this anymore. Is there anything I may do to enable that again?

---

### Post by jaayll on 2012-05-26
I have read around that this is a unity 5.12 problem and the solution is on downgrading to unity 5.10.
I have tried this but without success...

sudo apt-get install unity=5.10.0-*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Selected version '5.10.0-0ubuntu6' (Ubuntu:12.04/precise [i386]) for 'unity'
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 unity : Depends: libunity-core-5.0-5 (= 5.10.0-0ubuntu6) but 5.12-0ubuntu1.1 is to be installed
         Depends: unity-common (= 5.10.0-0ubuntu6) but 5.12-0ubuntu1.1 is to be installed
E: Unable to correct problems, you have held broken packages.

---

### Post by pensadorlouco on 2012-05-27
Thanks for answering me. I've tried it this morning but it didn't work, so I guess it may be a case of hoping they fix it in a newer version.

Best regards. :)

---

