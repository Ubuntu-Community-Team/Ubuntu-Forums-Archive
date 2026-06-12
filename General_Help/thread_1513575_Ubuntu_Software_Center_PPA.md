---
title: "Ubuntu Software Center PPA"
date: 2010-06-19
forum: General Help
---

### Post by su-37 on 2010-06-19
Hey ive been trying out a few PPas and now when i try to install or uninstall programs this comes up. I have followed the code and it keeps asking where i want to download the manual. What i would like to do is get rid of the PPAs or what ever needs to be done so i can use the SWC and install updates. Any ideas?

---

### Post by davidmohammed on 2010-06-19
open up a terminal

try

sudo dpkg --configure -a

or

sudo apt-get install -f

---

### Post by su-37 on 2010-06-19
tried the second one and it said to try the first one. Tried the first one and it said where do i want to download the manual to. WHich i am trying to stop. When i tell it where it downloads and i end up where i am to begin with.

---

### Post by davidmohammed on 2010-06-20
have a go at editing /etc/apt/sources.list and putting a # in front of the offending ppa.

after saving - try running combinations of

sudo apt-get -f update
sudo apt-get install -f

---

### Post by su-37 on 2010-06-23
I navigated to the software list and when i clicked on it the software sources manager came up. I removed the PPA's i thought were the problem. 

The first results in a download and when i try the second it asks me where i want to install the manual build. Youll be pleased to know that i can now install/deinstall sw and the problem as far as im concerned is fixed.

---

