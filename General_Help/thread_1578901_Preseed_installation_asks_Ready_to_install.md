---
title: "Preseed installation asks Ready to install"
date: 2010-09-21
forum: General Help
---

### Post by tolkeinknoxy on 2010-09-21
I've generated a preseed for my Ubuntu Lucid installation, its loading ubiquity automatically (from kernel parm automatic-ubiquity) and it fills in all the values from the preseed file its given.

 However it displays the Ubiquity page "Ready to Install" (I am using the kubuntu ubiquity package) and I have to click the button install for it to start. How can I get it to skip this and just start installing?

Many thanks.

---

### Post by tolkeinknoxy on 2010-09-21
I needed to include this at the bottom of my preseed file:
ubiquity ubiquity/summary note
This allowed it to miss the summary page and just install.

---

