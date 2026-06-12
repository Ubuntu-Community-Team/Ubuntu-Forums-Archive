---
title: "Bluetooth in 11.04"
date: 2011-04-25
forum: General Help
---

### Post by sugarat on 2011-04-25
I have installed 11.04 onto my iMac, which uses a BlueTooth keyboard and mouse. 

When attempting to set this up through the Bluetooth device manager, I keep getting a box pop up asking if I want to grant or deny access to my keyboard.  I keep hitting grant, but the box keeps coming back, and the keyboard never works.  How can I fix this?

I appreciate 11.04 is officially out yet, but it will be out very soon, so - does anyone know how to fix this?

---

### Post by Mark Phelps on 2011-04-26
You will get better and faster responses if you post your 11.04 questions to the Natty Development forum.  That is located at: Other Community Discussions --> Development & Programming --> Natty Narwhal Testing and Discussion

Good Luck

---

### Post by niko23 on 2011-04-28
try this

```
sudo killall bluetoothd
sudo bluetoothd
```

see also **[https://bugs.launchpad.net/system76/+bug/762964](https://bugs.launchpad.net/system76/+bug/762964)**

---

