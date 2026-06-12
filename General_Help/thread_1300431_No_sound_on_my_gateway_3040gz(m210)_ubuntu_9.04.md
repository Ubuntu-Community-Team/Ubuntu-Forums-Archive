---
title: "No sound on my gateway 3040gz(m210) ubuntu 9.04"
date: 2009-10-25
forum: General Help
---

### Post by blackmatrix00 on 2009-10-25
I'm new to Linux. I have a Gateway M210 laptop. Ubuntu installed drivers for everything including my sound card which it recognizes as Intel. I think its 82801DB-ICH4. Everything works except for my sound, even the audio controls work! . I've looked around here and there and cant find a solution, I hope the people here can help me. Any help would be much appreciated.

---

### Post by P4man on 2009-10-25
Try opening a terminal and run

```
alsamixer
```

use the arrow keys to navigate and change the sliders. Make sure PCM and surround channels are not muted.

---

### Post by blackmatrix00 on 2009-10-25
I've already done that and there is still no change, my sound is still not functional. Any thing else I can do?

---

### Post by buntuuser on 2009-12-12
I know it's been a while since your post, but for my gateway i went into sound preferences and went to the output tab and played around with the different connector options until it worked for me.  The one that worked for me was the "Analog Output / No Amplifier."  Good luck!

---

### Post by copenhagenlc on 2010-02-14
Thanks buntuuser that worked for me aswell

---

