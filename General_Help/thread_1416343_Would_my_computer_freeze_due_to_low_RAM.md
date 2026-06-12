---
title: "Would my computer freeze due to low RAM?"
date: 2010-02-26
forum: General Help
---

### Post by CharlesJWelsh on 2010-02-26
I was just browsing and it said something about it requiring 256MB of RAM to install the 9.04 OS. I was curious if that would cause the freezing during install and the freezing during usage of my laptop. Any ideas?

---

### Post by egalvan on 2010-02-26
Yes, insufficient RAM will cause freezes and lock-ups.

Insufficient RAM at install can be partially offset by pre-allocating a swap file (creating & formatting the swap partition before actual install),

by running the "install Ubuntu" option from the boot menu,
rather than the "run Ubuntu" option,

or installing using the "alternate" CD iso (this uses the least RAM during the install phase).


Insufficient RAM during actual usage is normally only cured by more RAM.
A large swap (2-4 times RAM) is only a stop-gap measure.
Low-RAM situations need swap.

---

### Post by Sef on 2010-02-26
From the [release notes]("http://www.ubuntu.com/getubuntu/releasenotes/904"):

> **System Requirements**

  The minimum memory requirement for Ubuntu 9.04 is 256 MB of memory. Note that some of your system's memory may be unavailable due to being used by the graphics card. If your computer has only the minimum amount of memory, the installation process will take longer than normal, but will complete successfully, and the system will perform adequately once installed. 
 Systems with less memory may be able to select "Install Ubuntu" from the boot menu to run just the installer, rather than the whole desktop, or may be able to use the alternate install CD. 

---

### Post by CharlesJWelsh on 2010-02-26
IF it were my RAM causing these freezes and lockups wouldnt it freeze while im using the live cd too?

---

### Post by |{urse on 2010-02-26
Sounds like you may benefit from running a memtest if you haven't already. Its on the main menu of the live-cd.

---

### Post by CharlesJWelsh on 2010-02-26
For learning purposes... What does the memtest do?

---

### Post by |{urse on 2010-02-26
It scans the ram for bad bits, this may explain the behavior you are describing.

---

### Post by CharlesJWelsh on 2010-02-26
Okay... and lets say I have "Bad bits" What will be the solution? More money out of pocket?

---

### Post by Sef on 2010-02-26
Read the [Memtest86]("http://memtest86.com/") site to understand more about how to read the memtest86 results.

---

### Post by CharlesJWelsh on 2010-02-26
Okay... I know for a fact I have bad bits. I have ran a memtest before for this issue.

---

### Post by zcrafts on 2010-02-26
Surely this does not sounds good for you.

---

### Post by |{urse on 2010-02-26
Yeah unfortunately you're going to need to replace that ram to get things running correctly again. =/

---

### Post by Kevbert on 2010-02-26
Before replacing the RAM check that its seated (fitted) correctly and refit if necessary and that the PC is clean of dust (carefully use a vacuum cleaner to remove any dust. The PC may work with Windows but may give occasional unexpected blue screens of death.

---

### Post by |{urse on 2010-02-27
yeah definitely do that as well.

---

