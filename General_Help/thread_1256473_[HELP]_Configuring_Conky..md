---
title: "[HELP] Configuring Conky."
date: 2009-09-02
forum: General Help
---

### Post by Letterbomb05 on 2009-09-02
Hi, noob linux user here :o

I've been trying to configure conky with my desktop after reading a tutorial on these forums. My first problem is that when I run conky, it appears a little bit too high on my desktop, this means it's slightly covered by my upper toolbar.

My second problem is that I have no idea how to reboot conky so it will use my updated script :S

Thanks for any help,
~Letterbomb05.

---

### Post by winotree on 2009-09-02
In your conkyrc script change these

gap_x 30
gap_y 30

to move your conky up and down *so that the value could be 5 or 35 or 40 or whatever it takes*, and look in here [http://ubuntuforums.org/showthread.php?p=5436679#post5437628](http://ubuntuforums.org/showthread.php?p=5436679#post5437628) to remedy your restart issues, especially this part

**STEP 2 - Setting up conky to autostart on boot.**

---

### Post by Letterbomb05 on 2009-09-02
Thanks, I can sort out getting the script to load on startup ok, I just need to know how to reboot the script so it updates once I've modified it.

---

### Post by winotree on 2009-09-02
> **Letterbomb05 said:**
> Thanks, I can sort out getting the script to load on startup ok, I just need to know how to reboot the script so it updates once I've modified it.
One thing I did was to right-click the startup script in file manager -- not elegant or overly practical but effective.  ;)

---

