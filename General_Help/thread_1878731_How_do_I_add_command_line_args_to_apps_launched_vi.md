---
title: "How do I add command line args to apps launched via dash?"
date: 2011-11-10
forum: General Help
---

### Post by reuben on 2011-11-10
I want to add a command line argument to chrome's startup, given that I am writing a javascript app which I need to debug, and find that the "page is unresponsive" dialog gets in my way.

The ubuntu menu editor does not seem to let me edit the properties for chromium (if I right click and choose properties, nothing happens.)

Where are the .desktop (?) files held, so that I can edit it directly?

Thanks

---

### Post by satanselbow on 2011-11-10
in a terminal:

```

gksu nautilus /usr/share/applications

```

you need to add your arguments to the "Exec=" line ;)

---

### Post by reuben on 2011-11-10
Thanks!

---

