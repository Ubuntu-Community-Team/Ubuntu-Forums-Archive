---
title: "Need basic help with display resolution settings"
date: 2010-02-01
forum: General Help
---

### Post by DrScum on 2010-02-01
After messing around with display settings caused by an uncooperative beamer the correct display setting isn't available anymore.

Ubuntu 9.04 running on Dell Inspirion 6400. 

Display used to be just fine, but now the maximum resolution available is 1024x768 (4:3) which leave me with two black bars to the left and the right of the display.

Help is appreciated.

---

### Post by audiomick on 2010-02-01
You should perhaps post the specs of your graphic card. That might help people to assist you.

---

### Post by DrScum on 2010-02-01
How would I get those?

---

### Post by audiomick on 2010-02-01
Try
```
lspci
```
in a terminal. Post the output here.

---

### Post by DrScum on 2010-02-01
here the relevant lspci output

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

---

### Post by Jotham on 2010-02-01
The instructions [here]("https://wiki.ubuntu.com/X/Config/Resolution") should help you change the resolution.

---

