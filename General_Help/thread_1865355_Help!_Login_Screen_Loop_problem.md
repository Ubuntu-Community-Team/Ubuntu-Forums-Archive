---
title: "Help! Login Screen Loop problem"
date: 2011-10-20
forum: General Help
---

### Post by HQiu on 2011-10-20
Hi all,

I cannot log in my Ubuntu Desktop 11.10 w/ my account and password, but can log in w/ Guest Session in the Login Screen. After entering the correct password of my account on the Login Screen, the Login Screen will disappear, just like a normal login does, but the Login Screen will come back again in seconds, and that will continue as a loop! I'm not sure it was the problem of the upgrades I made today since everything went so smoothly until today.
Any clues? Thanks!

Haibo

---

### Post by HQiu on 2011-10-20
Solved! It was Byobu! The cause is I didn't stop Byobu from auto-starting before I removed it. So my solution is: re-install the Byobu under tty1, login to the xwindow desktop, run "byobu-disable" before removing it. And now I can log in Ubuntu from the Login Screen.

---

