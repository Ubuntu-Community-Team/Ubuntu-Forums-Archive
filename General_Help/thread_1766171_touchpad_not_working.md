---
title: "touchpad not working"
date: 2011-05-24
forum: General Help
---

### Post by srinathduraisamy on 2011-05-24
Hi 

I have upgraded my ubuntu from 10.10 to 11.04 in my dell vostro 1510 laptop. After upgrading my touchpad is not working.

any suggestions will be very helpful.

regards
Srinath

---

### Post by idoitprone on 2011-05-24
[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

I do not know much about configure touch pad, but i will only help to get you started.

```
xinput list
```

I want to know if the touch pad is detected or bios disable. It should say synpatic or something. btw, next time write down your hardware, less googling for the people trying to help.


```
synclient  | grep -i touch

```

check if TouchpadOff value = 1
If it does, then

```
synclient TouchpadOff=0
```

if you wish for a gui
```
sudo apt-get install gsynaptics

```

---

