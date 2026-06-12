---
title: "TTY Error Ubuntu 10.04"
date: 2010-05-11
forum: General Help
---

### Post by sicpsnake on 2010-05-11
Whenever I enter a TTY all of the text is big and pixelated, rendering it unreadable and unusable. This only became a problem after updating to 10.04. Is there any way to fix this? It is a pain in the *** to not be able to use the TTY. Help is much appreciated. :confused:

---

### Post by sicpsnake on 2010-05-11
Bump.

---

### Post by sicpsnake on 2010-05-11
Never mind. I fixed it. Uncommented "GRUB_TERMINAL=console" and now it works.

---

### Post by ahso4271 on 2010-05-29
I've the same. Where did u change this? Thnks

---

### Post by Sentello on 2010-06-23
i have same problem, but uncommented "GRUB_TERMINAL=console" not  solve problem:confused:

---

### Post by Elding Nyr on 2010-08-25
sicpsnake, did you remember to run the command update-grub as root after uncommenting that line?

---

