---
title: "QGIS 1.7 update is faulty - want to revert to 1.6!"
date: 2011-06-15
forum: General Help
---

### Post by Robin Lovelace on 2011-06-15
Hello, 

The constant evolution and automatic update of programs is a huge advantage of Ubuntu, and one of the reasons I use it. However, I have found QGIS 1.7 automatic update (a few days ago) does not work. So I want to re-install the previous verion (1.6) but cannot find it anywhere. Any ideas?

The detail is that when I open a large .shx vector layer, the program grinds to a near halt and eventually freezes. This is odd as I'm using a fast processor (Pentium i5) and 4 Gb of RAM. It's a 64 bit machine.

The general point is how do you install previous versions of software if automatic updates are not as bug-free as developers think. This should also be a bug on QGIS development website, but I'm sure it's of general interest to Ubuntu users relying on automatic updates.

Thanks - and hope the general point of this question does not make it too specific for this "General Help" category.

Robin

---

### Post by aarongc on 2011-06-20
I have the same problem, because of a different bug in 1.7. Essentially, legends in the map composer view are broken -- symbols are the wrong size, and some of the features from 1.6 have disappeared. I am looking for 1.6 packages all over the net but can't find them!

---

### Post by Robin Lovelace on 2011-06-21
Thanks for this Aaron, it's good to know it's not just me who would like to revert to QGIS 1.6. Please keep your eyes open for 1.6 packages and let me know if you find any.

More important for the future of Ubuntu is to ask how did this happen? For me 2 important failings have happened:

1) QGIS 1.7 was included in the automatic updates without being properly tested. It's important that users trust Ubuntu to select worthwhile and bug-free updates, so some testing needs to go beforehand. The high quality of most updates makes me think this happen. How did QGIS slip through the net?

2) There are no "revert to previous edition" options available in the Ubuntu software centre.

Please could someone comment on these general points. More urgently, where is this elusive QGIS 1.6 package?

---

### Post by Robin Lovelace on 2011-06-22
Just to let you know this issue has been resolved - deselect Ubuntugis from repository lists, add qgis repository and install qgis from synaptic. If there is any way to remove the faulty version of qgis 1.7 from Ubuntugis I'd be interested to know.

This answer came from qgis forum here [http://forum.qgis.org/viewtopic.php?f=2&t=8840&p=19942#p19942](http://forum.qgis.org/viewtopic.php?f=2&t=8840&p=19942#p19942)

---

