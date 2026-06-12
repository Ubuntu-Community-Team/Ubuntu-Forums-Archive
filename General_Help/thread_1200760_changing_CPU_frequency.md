---
title: "changing CPU frequency?"
date: 2009-06-30
forum: General Help
---

### Post by cyorg on 2009-06-30
My CPU runs at 800 MHz by default, but I'm able to change it to 1.8 GHz. The problem is that whenever I reboot my laptop, it resets back to 800 MHz. How can I make 1.8 GHz the default frequency?

---

### Post by utnubuuser on 2009-06-30
Right-click the panel  (gnome), select "Add to Panel", scroll down, find CPU frequency monitor. select add.

Once the applet is on the panel, click to select frequency.

...I know that's not what you asked...

With that applet you might be able to set the frequency, then select System>>Preferences>>Sessions>>Options>>Remember currently running applications.

...and I'm sure there is a more sophisticated way of setting the frequency.

---

### Post by cyorg on 2009-06-30
I've added that to my panel, and it works, but if I restart my computer it goes back to 800 MHz. Is there a way to set it so that I don't have to do that every time?

---

### Post by colau on 2009-06-30
> **cyorg said:**
> I've added that to my panel, and it works, but if I restart my computer it goes back to 800 MHz. Is there a way to set it so that I don't have to do that every time?
How do you change it from 800MHz to 1.8GHz?

---

### Post by DeMus on 2009-06-30
> **colau said:**
> How do you change it from 800MHz to 1.8GHz?

Can you switch off the frequency scaling using the program you just added to your panel? I did that, now my cpu's run constantly on maximum.

---

### Post by cyorg on 2009-06-30
> **colau said:**
> How do you change it from 800MHz to 1.8GHz?
Right click panel >> select add to panel >> scroll down and select CPU frequency scaling monitor.

> **DeMus said:**
> Can you switch off the frequency scaling using the program you just added to your panel? I did that, now my cpu's run constantly on maximum.
I don't see an option to turn it off with that program. How did you turn it off?

---

### Post by DeMus on 2009-06-30
> **cyorg said:**
> Right click panel >> select add to panel >> scroll down and select CPU frequency scaling monitor.


I don't see an option to turn it off with that program. How did you turn it off?

Oops, sorry, I made a big mistake. I switched it off in BIOS not using this software. Now whenever I start this program it tells me I switched it off.
I use a desktop and you wrote you are using a laptop. The BIOS is probably completely different so it might not work, or might not even be possible to change it.

---

### Post by mcduck on 2009-06-30
> **cyorg said:**
> My CPU runs at 800 MHz by default, but I'm able to change it to 1.8 GHz. The problem is that whenever I reboot my laptop, it resets back to 800 MHz. How can I make 1.8 GHz the default frequency?

Just to inform you, the default behavior for CPU frequency scaling is to run at minimum frequency when CPU isn't used, and switching automatically to full speed when something actually gives the CPU something to work with.

Working this way gives you exactly the same performance as running at full speed, but with less produced heat (meaning also less noise if your cooling adapts to temperature), and longer battery life on laptops. Usually there's no reason to change this behavior.

---

### Post by colau on 2009-06-30
> **cyorg said:**
> Right click panel >> select add to panel >> scroll down and select CPU frequency scaling monitor.

If I add this to the top panel ,I get a message first.
But the icon above always indicates that 100% cpu is being used and frequency scaling is unsupported.

---

