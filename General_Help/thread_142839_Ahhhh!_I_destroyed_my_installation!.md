---
title: "Ahhhh! I destroyed my installation!"
date: 2006-03-11
forum: General Help
---

### Post by DigitalFudge on 2006-03-11
Can someone help me please?

I was playing around, and I changed my repositories from breezy to dapper.. Ran apt-get update, apt-get dist-upgrade... and anyway..

Now my box is a mess of unmet dependencies and other nastiness! I'm sure it's fixable, as long as I can start on a clean slate - I just dont' want to reinstall... 

How can I delete -ALL PACKAGES- except for the basic basic packages just required to boot the system?

Thank you guys!

---

### Post by Xian on 2006-03-11
I would first try this...

Open Synaptic and goto Settings > Preferences
Open the Distribution tab.

Now, choose "Prefer Versions From" and select Breezy.
Try to Reload sources and Mark All Upgrades.

---

### Post by az on 2006-03-11
What does
sudo apt-get -f install
say?

---

### Post by DigitalFudge on 2006-03-11
Hey guys, thanks for the help-- But I just decided to do a fresh install instead.

Guess I'm not really ready for dapper just quite yet :)

---

