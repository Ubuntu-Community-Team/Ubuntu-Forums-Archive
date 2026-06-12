---
title: "Remote Desktop on 9.04 not working"
date: 2009-09-30
forum: General Help
---

### Post by lout on 2009-09-30
When i connect from windows or osx (same result) i see ubuntu desktop but example when open folder nothing hapend so i close conection(on windows or osx) then  start vnc again i see ubuntu desktop with open folder from last time but still not working how to fix this

---

### Post by Giblet5 on 2009-09-30
I need a better description of the problem.

How are you trying to "open folder"? Are you clicking on the Places menu and selecting something? Does the menu pop up? Does the mouse do *anything* (right click, left click, etc)?

---

### Post by XCan on 2009-09-30
This is a known bug in Jaunty and the bug will exist in Karmic as well. The simple and perhaps the least sucky workaround is for you to simply disable visual effects. Patches for xorg are available, but it doesn't look like it's going to be included anytime soon. See [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/353126](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/353126)

---

