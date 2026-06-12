---
title: "&quot;Extra Effects&quot; conflicts with OpenGL"
date: 2010-09-28
forum: General Help
---

### Post by Ancanus on 2010-09-28
Hello.

Whenever I try to run any of my OpenGL programs with **Settings -> Appearance -> Visual Effects: Extra**, the program window flickers and disappears. However, if I turn my effects to Normal, my OpenGL programs run smoothly.

Any way to have both on at the same time?

```

$ fglrxinfo display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 5800 Series 
OpenGL version string: 1.4 (4.0.10237 Compatibility Profile Context)
```

Thanks...

---

### Post by Tylerjd on 2010-09-28
I would try a few things, but as I have NVIDIA in my laptop, there might be a *slight* difference...
A) make sure your firmware on the graphics card is up-to-date 
and/or 
B) see if you have the correct restricted drivers installed, as the graphics card may need some proprietary drivers...

---

### Post by Ancanus on 2010-09-28
> **Tylerjd said:**
> I would try a few things, but as I have NVIDIA in my laptop, there might be a *slight* difference...
A) make sure your firmware on the graphics card is up-to-date 
and/or 
B) see if you have the correct restricted drivers installed, as the graphics card may need some proprietary drivers...

Hello Tylerjd, thank you for the prompt response.

I do have the latest restricted drivers installed for ATI. Any other ideas?

```

$aptitude show fglrx
Package: fglrx                           
New: yes
State: installed
Automatically installed: no
Version: 2:8.780-0ubuntu2
...
```

---

### Post by I8NY on 2010-10-12
I have the same problem and have tried to fix it 5 times so far.(All have failed)  I have a ATI 4850 and i will get it with every game except maybe one that is using openGL another way.  I have tried the ubuntu hardware drivers and the ATI website ones. The ATI driver did fix it untill after a few reboots and installing adobe reader.  I will update to 10.10 and hope that this bug will only stay in 10.04 when i had this problem start.  Hope you find the solution.

---

