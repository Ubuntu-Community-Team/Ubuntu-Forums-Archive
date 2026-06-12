---
title: "Can't wake up monitor after Suspend or Hibernate!! Help!!"
date: 2009-11-19
forum: General Help
---

### Post by Ubu4moi on 2009-11-19
I'm running Ubuntu 64 bit Ultimate Edition 2.0 on an HP Pavilion AMD Athlon X2. When I Suspend the computer I can't wake up the IBM monitor. I tried turning it off and back on but it wouldn't wake up. I have to re-start the computer everytime. Anyone knows about this bug?

---

### Post by undecim on 2009-11-20
I had the same issue with FaunOS on an IBM notebook. I worked around it by pressing ctrl+alt+f1 to go to a terminal, and then alt+f7 to go back to Xorg.

This causes the video card to reinitialize and may wake your monitor back up.

---

