---
title: "Scanner not detected by Xsane but video card is"
date: 2010-05-07
forum: General Help
---

### Post by sofasurfer on 2010-05-07
Using xsane with HP scanjet 3970 scanner. It used to be that when I plugged the scanner in and started the xsane a window would come up asking if I wanted to use my HP scanner or my Hauppauge video card. Well, that window no longer comes up and the Xsane wants to use my video card. When I try to "scan" the program closes and all the windows associated with it disappear.
What happened?

---

### Post by dimmak on 2010-05-19
I have a hp psc 1315 all-in-one and I fixed the problem by installing hplip.

```
sudo apt-get install hplip
```

---

