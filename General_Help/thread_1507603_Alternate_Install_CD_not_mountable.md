---
title: "Alternate Install CD not mountable?"
date: 2010-06-11
forum: General Help
---

### Post by GrantStoner on 2010-06-11
I've upgraded to the new 10.04, and when I have the Alternate CD in, it shows on my desktop, and I can search all the contents of the CD, so I know it's registering. But when I try to install anything, via the terminal, .deb packages, synaptics package manager, it always asks me to insert the CD. Then I click ok and it says it's not mountable, even though I know it is because it's on my desktop. Anyone else having this issue?

---

### Post by dcstar on 2010-06-12
> **GrantStoner said:**
> I've upgraded to the new 10.04, and when I have the Alternate CD in, it shows on my desktop, and I can search all the contents of the CD, so I know it's registering. But when I try to install anything, via the terminal, .deb packages, synaptics package manager, it always asks me to insert the CD. Then I click ok and it says it's not mountable, even though I know it is because it's on my desktop. Anyone else having this issue?

Make sure you don't have an entry for an **old** version CD in your software sources.

---

### Post by wilee-nilee on 2010-06-12
> **dcstar said:**
> Make sure you don't have an entry for an **old** version CD in your software sources.

This is correct if you have installed remove the cd tick off the cd in software sources, and run ```
sudo apt-get update
``` then ```
sudo apt-get upgrade
```

---

### Post by GrantStoner on 2010-06-12
I've done this, but it still comes up with an error. And I've never had a problem before with any other version of Ubuntu using the same method. Is it possible has anything to do with me having a slimline drive instead of one that actually pops open and you have to manually close it?

---

