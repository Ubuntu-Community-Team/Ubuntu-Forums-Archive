---
title: "HOWTO: Fix PPA's broken after updating to 11.10"
date: 2011-10-27
forum: General Help
---

### Post by Scouto on 2011-10-27
If, like me, you've found that several of your PPA's refuse to update after upgrading your Ubuntu, there's an easy fix.

1. Open the dash and type 'software sources'. (without the ')

2. Click the 'other software' tab and find the trouble maker, highlight it and click 'edit'.

3. In the 'distribution' field change 'oneiric' to 'natty' and hit ok.

4. Now just reload the package list or head to a terminal and run 'sudo apt-get update' (you might be prompted for your password) and you should find everything updates as it should.

Hope this helps!

---

