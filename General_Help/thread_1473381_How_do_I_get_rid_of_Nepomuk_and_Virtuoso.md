---
title: "How do I get rid of Nepomuk and Virtuoso"
date: 2010-05-05
forum: General Help
---

### Post by GuiGuy on 2010-05-05
OK, so I had to a clean install and I have the spiffy 10.4 kubuntu thing going. Only thing is firefox, something called nepomukserver and virtuoso-t make sure my AMD Phenom is absolutely too exhausted to do anything else. 

I got rid of firefox (thanks for Chrome, Mr. Google) but what do I do about the nepomucky thing. It's absolutely rampant. The hard disk never stops chattering, it's chewing up resources <sigh>. How do I get rid of the nepomuckserver? 

whispers: help?

TIA

---

### Post by emamm2008 on 2010-05-06
Same problem here.  They keep eating up all available resources to the point of getting my linux box on its knees.
Kill -9 won't work since they keep coming back.

If you get an answer, please let me know.

Cheers

Ed

---

### Post by kernco on 2010-05-06
In system settings, go to the Advanced tab and then the desktop search section (it has the nepomuk icon).  In the basic settings tab, uncheck "Enable Strigi Desktop File Indexer" to turn off Virtuoso.  You can also uncheck "Enable Nepomuk Semantic Desktop" but having that checked shouldn't cause any performance problems, it just enables the ability to tag and rate files.

---

### Post by GuiGuy on 2010-05-06
> **kernco said:**
> In system settings, go to the Advanced tab and then the desktop search section (it has the nepomuk icon).  In the basic settings tab, uncheck "Enable Strigi Desktop File Indexer" to turn off Virtuoso.  You can also uncheck "Enable Nepomuk Semantic Desktop" but having that checked shouldn't cause any performance problems, it just enables the ability to tag and rate files.

I don't see either of those options under System Settings > Advanced

---

### Post by bertoid on 2010-05-06
Thanks for putting this fix up. Not sure why this garbage was enabled by default, but it slowed my system to a crawl. Hopefully it'll be better now...

---

### Post by kernco on 2010-05-06
> **GuiGuy said:**
> I don't see either of those options under System Settings > Advanced

System Settings > Advanced > Desktop Search

---

### Post by JohnLloydJones on 2010-05-16
Can anyone please explain what value Nepomuk/Virtuoso has for a user that justifies chewing so much CPU? The nepomuk site is full of fancy words, but nowhere can I actually find out what it is supposed to do for me.

---

### Post by king4 on 2011-03-23
There is an alternative to switch of the indexing under 10.04 lucid. If you see the nepomuk icon in the top panel, click on it and select the option *Suspend File Indexing* of *Prefereces -> *uncheck *Enable file indexing*.

---

### Post by Yellow Pasque on 2011-03-23
FWIW, the CPU usage issues with Nepomuk are supposedly fixed in KDE 4.6.x: [http://phoronix.com/forums/showthread.php?29940-KDE-4.6.0-Has-Arrived](http://phoronix.com/forums/showthread.php?29940-KDE-4.6.0-Has-Arrived)

---

### Post by GuiGuy on 2011-03-23
I've gone back to the gnome desktop. The flakyness and weird behaviour issues with the KDE desktop simply outweigh its superior (IMO) look and feel. And I couldn't get used that other resource hog, Amarok, either.

---

