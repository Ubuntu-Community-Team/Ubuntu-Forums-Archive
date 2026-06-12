---
title: "How to list USB devices through terminal?"
date: 2010-11-11
forum: General Help
---

### Post by Vigh on 2010-11-11
How do I list all USB devices in the terminal? Is there a maximum number of usb devices? I have a MIDI controller which normally works perfectly with ALSA which doesn't seem to be detected. Have lots and lots of USB devices going.

Regards

---

### Post by Crusty Old Fart on 2010-11-11
If they are mounted, they should show up in mtab.
```

cat /etc/mtab

```

---

### Post by Hippytaff on 2010-11-11
Also
```

lsusb

```:-)

---

### Post by Crusty Old Fart on 2010-11-11
Yeah...lsusb...much better.

But, being the dog that I am, I often have cat on the brain and make him work at every opportunity. :cool:

---

