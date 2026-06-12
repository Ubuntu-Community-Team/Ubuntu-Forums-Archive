---
title: "JAVA Applications stopped working - Lucid"
date: 2010-05-02
forum: General Help
---

### Post by crjackson on 2010-05-02
Fresh install of Lucid.  JAVA6 installed from the Ubuntu repository, and the web plugin works as desired.

JAVA applications like JBidwatcher and FrostWire have stopped working from the Applications Launchers.  I checked them out and they are fine.

If I right click and till the app to launch with Sun Java JRE it works.

It seems to be a path issue for JRE but I don't know how to fix this.  It was working fine a couple of days ago but stopped after a reboot.

Numerous reboots don't affect the problem.  I've tried.

Please help.

---

### Post by crjackson on 2010-05-02
With trial and error, I managed to get it working with:

```
sudo update-java-alternatives --set java-6-sun
```

---

