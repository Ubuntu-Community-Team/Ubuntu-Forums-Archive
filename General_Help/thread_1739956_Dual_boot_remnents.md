---
title: "Dual boot remnents"
date: 2011-04-26
forum: General Help
---

### Post by rmcellig on 2011-04-26
I had set up dual boot XP/Ubuntu on my wife's PC using (and I can't remember the bane off hand) an application I installed on her PC that would allow me to dual boot. I deleted the application with Add/Remove applications but when I restart her PC, I still see what looks like GRUB displaying two options. Windows XP and Windows. I would love to get rid of this so that all she has to do is turn on her PC and boot right into XP. How can I do this?

---

### Post by seawolf167 on 2011-04-26
Easiest method to remove GRUB and have the Windows boot loader work correctly is to insert your Windows cd, enter the recovery console, then type

```
fixmbr
fixboot
```

then restart

---

### Post by rmcellig on 2011-04-27
I can't find my XP Pro disk at the moment. Can I boot from my Partition Magic live CD or my Clonezilla CD and do it? If so, what do I have to do?

---

