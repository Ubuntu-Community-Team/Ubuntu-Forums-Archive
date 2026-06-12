---
title: "Plymouth with on-board intel graphics"
date: 2011-06-05
forum: General Help
---

### Post by whalogreg on 2011-06-05
After upgrading to Natty, my Plymouth screen has gone from working normally, to the logo being text-based and off centered at the top left portion of my screen. I have seen many fixes for this where the problem seems to be Nvidia or ATI related. I, on the other hand, have on-board intel graphics, with no third party drivers installed. Any idea where I could start with this problem?

---

### Post by whalogreg on 2011-06-06
bump

---

### Post by whalogreg on 2011-06-08
bump

---

### Post by whalogreg on 2011-06-10
bump

---

### Post by szale9001 on 2011-06-28
also experience this problem. Are there any bug reports?

---

### Post by Lekensteyn on 2011-06-28
Symptoms:
- The boot "splash" is positioned in the upper left corner
- There is no logo or other graphical stuff, everything is just text
- You're using an Intel graphics card (like the i5-xxx and i7-xxx series)
- On shutdown, plymouth shows up correctly

For a work-around see:
[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/770371/comments/4](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/770371/comments/4)

An analysis can be found at:
[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/770371/comments/3](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/770371/comments/3)

---

### Post by whalogreg on 2011-07-04
> **Lekensteyn said:**
> Symptoms:
- The boot "splash" is positioned in the upper left corner
- There is no logo or other graphical stuff, everything is just text
- You're using an Intel graphics card (like the i5-xxx and i7-xxx series)
- On shutdown, plymouth shows up correctly

For a work-around see:
[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/770371/comments/4](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/770371/comments/4)

An analysis can be found at:
[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/770371/comments/3](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/770371/comments/3)


That did it! Thanks a bunch!

---

