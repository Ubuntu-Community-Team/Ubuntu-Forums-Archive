---
title: "problems with xming coonecting to Linux"
date: 2009-07-21
forum: General Help
---

### Post by briandu on 2009-07-21
Folks,
 
using Putty I connect ot a server - session reference in Windows is 0, so no problem. I can open xclock and no prob.
 
When I switch user via sudo then a prob occurs. 
 
Using sudo user when invoking xclock we recieve messgae of protocol error. The win reference is 10:0 - which is wrong of course.
 
forcing the display with:
DISPLAY=my.ip.addr:0.0
export DISPLAY
 
we get a protocol error.
 
It seems the xserver cannot determine the protocol / security token to the xming on Windows correctly for some reason.
 
Any ideas?
 
Suggested was the .Xauthority file - can this be right?

---

### Post by briandu on 2009-07-21
Bump!
 
Anybody have a view or suggest where to look?
 
thx

---

