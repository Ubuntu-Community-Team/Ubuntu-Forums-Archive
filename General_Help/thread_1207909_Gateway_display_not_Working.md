---
title: "Gateway display not Working"
date: 2009-07-08
forum: General Help
---

### Post by Prominence on 2009-07-08
I installed Ubuntu on my brother's computer, it's 64 bit and uses an AMD, up until the time I installed the Nvidia Graphics Card driver, the display worked, though off center, after installing the driver no display is visible but the system is working, at the top of the monitor a SLIM sight of the top panel is visible, all under that is black. When launching an application via random clicking the black would flash white. Is it the monitor? Is a new one needed? Or is there a fix? Reply quickly please.

[He uses the computer for his business]

---

### Post by Woody1987 on 2009-07-08
if you need to use it quickly, try going into recovery mode, and choosing xfix. This should stop the nvidia driver from loading and may allow you to get back to how it was before you installed it.

---

### Post by Prominence on 2009-07-08
How do I get into recovery mode?

---

### Post by jdeppel on 2009-07-08
When you boot up your system, your GRUB Menu should have a listing of your available Linux kernels in it. Select the newest (highest number) that has "Recovery Mode" in parenthesis next to it.

---

### Post by Prominence on 2009-07-08
It doesn't give me the option, how do I access it otherwise?

---

### Post by jdeppel on 2009-07-08
As your computer is booting up, try pressing ESC when you get to the screen that says:

GRUB Loading Stage1.5.

GRUB Loading, please wait...
Press 'ESC' to enter the menu... 3

You'll have to be fairly quick with it...it times out after 3 seconds. That should drop you to your GRUB menu.

---

### Post by Prominence on 2009-07-08
Oh ok thank you very much

---

### Post by jdeppel on 2009-07-08
No problem.
:D

---

