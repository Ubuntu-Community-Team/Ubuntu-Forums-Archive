---
title: "block internet, except for a few domains."
date: 2010-11-04
forum: General Help
---

### Post by Heeter on 2010-11-04
Hi all,

This is for a 10.10 desktop computer.

I am wondering how is the best way to block off the entire internet, except for a couple of domains.

This particular desktop will be located in the subcontractor office and the boss is asking to restrict their internet access to only a handful of domains (about 6 domains).

Any help will be greatly appreciated.

Thanks

Heeter

---

### Post by evilsoup on 2010-11-04
1) Install Firestarter (sudo apt-get install firestarter)
2) Open it up and navigate to the 'Policy' tab
3) Set to 'Restrictive by Default'

You can set exceptions by right-clicking on the box under 'Allow connections to host' and selecting 'Add rule'.

I haven't tried this personally, but it *should *work. There are other tools than firestarter, and you can also do this all through the command-line (don't know how, though).

---

