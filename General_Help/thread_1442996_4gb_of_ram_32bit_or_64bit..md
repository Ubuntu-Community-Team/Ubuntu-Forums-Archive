---
title: "4gb of ram 32bit or 64bit."
date: 2010-03-30
forum: General Help
---

### Post by MonteCarloZ on 2010-03-30
Going to do a fresh install on a 4gb laptop. Is linux like Windows and will only display 3.4gb on 32bit version or will it show the entire 4gb? 

PS: How is the beta version of flash doing on 64bit, I have not read anything lately on that. ?

Thank u

---

### Post by Sin@Sin-Sacrifice on 2010-03-30
You can enable something-or-other to utilize all 4 in x86 but I hear it's not recommended on home PC's so I would go with x86_64. Flash is not to bad with some tweaking. If flash from the repos is buggy then use this script to get the beta from adobe.

---

### Post by Arand on 2010-03-30
Yes, plain 32bit can per definition only get around ~3.2GB of RAM.

However there's always PAE: [https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)
- Arand

---

### Post by MonteCarloZ on 2010-03-30
Ok thanks guys. I will go with x64 version of 9.10 and upgrade to 10.04 when it comes out.

---

### Post by speedwell68 on 2010-03-30
I have recently upgraded my desktop PC to 4Gb or ram and it only detected 3.4Gg.  I installed x64 and TBH found it a pain.  So I reverted back to 32bit 9.10 and low and behold it installed the PAE kernel by default.  That how to on enabling PAE should work a treat, jusy make sure you have a proper backup first.

---

