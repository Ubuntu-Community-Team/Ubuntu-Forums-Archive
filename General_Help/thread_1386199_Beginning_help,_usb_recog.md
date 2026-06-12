---
title: "Beginning help, usb recog"
date: 2010-01-20
forum: General Help
---

### Post by jwright3 on 2010-01-20
I just installed 9.10 due to multiple failures via windows. i briefly tried kubuntu a while ago and didn't like it. So far, though, I really like this. 
I was wondering if anyone could shed some light on a gamepad issue--I have an old Sidewinder Gamepad (usb) and can't get it to work. The light on the controller turns on so the usb port itself is fine. Any ideas?

---

### Post by synapsys on 2010-01-20
What application are you trying to use your gamepad with?

What is the output of 

```
ls /dev/input
```

---

### Post by jwright3 on 2010-01-21
The emulators from Ubuntu software center (Haven't tried on PSX yet but no luck with 64Plus)

by-id    event0  event10  event2  event4  event6  event8  js0   mouse0
by-path  event1  event11  event3  event5  event7  event9  mice  mouse1

---

