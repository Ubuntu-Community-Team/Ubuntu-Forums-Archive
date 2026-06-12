---
title: "Where are the rest of the repositories listes?"
date: 2010-04-11
forum: General Help
---

### Post by adcwoef on 2010-04-11
If you open up the graphical "Software sources" and go to the tab "Other Software" 10 repos are listed. However these repos are not listed in /etc/apt/sources.list. So where are these lines stored if not there (where I expected them to be).

---

### Post by darolu on 2010-04-11
They are at: /etc/apt/sources.list.d/ each file contains the repositories lines; is a more secure way to handle them.

---

### Post by wojox on 2010-04-11
Look in /etc/apt/sources.list.d/

---

### Post by adcwoef on 2010-04-11
Ah thanks a lot!

---

