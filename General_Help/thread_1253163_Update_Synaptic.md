---
title: "Update Synaptic"
date: 2009-08-29
forum: General Help
---

### Post by RedSingularity on 2009-08-29
Quick question, how do i update the packages available in synaptic.  I added new repositories but the packages wont show in synaptic.

---

### Post by NoaHall on 2009-08-29
There should be a "refresh" or "reload" button on the top left had side

---

### Post by wojox on 2009-08-29
Did you add them through System > Administration > Software Sources > Third-Party Software and then checked the boxes.

---

### Post by RedSingularity on 2009-08-29
I have tryed both suggestions but no dice.

---

### Post by RedSingularity on 2009-08-29
Oh i got it.  

This has to be entered into terminal.

```
sudo update-apt-xapian-index
```

I have never seen this command before.  Can anyone explain?

---

