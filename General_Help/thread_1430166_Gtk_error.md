---
title: "Gtk error"
date: 2010-03-15
forum: General Help
---

### Post by Da CalebMan on 2010-03-15
Hi guys! Long story...

You know that RGBA engine for murrine? I downloaded it. But as it said in the overview, there's a catch. Some programs don't function properly with it. So it suggested adding non-cooperative programs to the blacklist, which prevents those programs from using RGBA. Thinking this was the reason flash wasn't working in Google-Chrome, I added 'chromium-browser --enable-plugins' to the blacklist. I rebooted and now I'm stuck at GDM. I login, it looks like it's working, until it goes back to GDM and prompts me for my username and password.

So that's the problem. If I press 'ctrl+alt+F1' to bring me to a terminal, how do I edit the blacklist without opening a GUI?

Anyone have a plan?

Thanks in advance!:D

---

### Post by dcstar on 2010-03-15
> **Da CalebMan said:**
> Hi guys! Long story...

You know that RGBA engine for murrine? I downloaded it. But as it said in the overview, there's a catch. Some programs don't function properly with it. So it suggested adding non-cooperative programs to the blacklist, which prevents those programs from using RGBA. Thinking this was the reason flash wasn't working in Google-Chrome, I added 'chromium-browser --enable-plugins' to the blacklist. I rebooted and now I'm stuck at GDM. I login, it looks like it's working, until it goes back to GDM and prompts me for my username and password.

So that's the problem. If I press 'ctrl+alt+F1' to bring me to a terminal, how do I edit the blacklist without opening a GUI?

Anyone have a plan?

Thanks in advance!:D

If you want to edit a text file:

```
sudo nano filename
```

---

### Post by themusicalduck on 2010-03-15
Did you edit the file at /etc/profile.d/gtkrgba.sh?

To edit it again from the command line, you could try using ```
sudo nano /etc/profile.d/gtkrgba.sh
``` which will open up the file in a terminal based editor.

If you can't persuade that to work, then you could always boot with a live CD and edit it from that.

The problem might have been because you included --enable-plugins and really you just want the program name only.

By the way, if you blacklist the program ```
exe
``` it should fix your flash problem. I fixed it the same way when I installed RGBA :)

---

### Post by Da CalebMan on 2010-03-15
Thanks guys!:D I thought of using the live cd, but I couldn't find it! Anyway, fixed it with Nano. Thanks again!;)

---

