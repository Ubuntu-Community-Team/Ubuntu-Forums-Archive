---
title: "Remote desktop &quot;Allow other user to control your desktop&quot;"
date: 2009-09-17
forum: General Help
---

### Post by Plexus81 on 2009-09-17
The problem that got is that I only view a screenshot of the screen. The screen never updates when I ex. press the ubuntu menu, try to type in text ex.. 

What's wrong?

I've got no problem connecting to the server. I've also put a check mark on the options:
- Allow other user to view your desktop
- Allow other user to control your desktop

---

### Post by XCan on 2009-09-17
I think you're running into the bug discussed [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/353126](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/353126) . Basicly, the short and easy workaround is to disable visual effects. There are other alternatives and patches, such as using a vncserver with xdamage flag support, or patching Xorg itself.

---

### Post by Plexus81 on 2009-09-17
> **XCan said:**
> I think you're running into the bug discussed [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/353126](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/353126) . Basicly, the short and easy workaround is to disable visual effects. There are other alternatives and patches, such as using a vncserver with xdamage flag support, or patching Xorg itself.

I diabled the "Visual effects" and it works like a charm! Thanks!

---

