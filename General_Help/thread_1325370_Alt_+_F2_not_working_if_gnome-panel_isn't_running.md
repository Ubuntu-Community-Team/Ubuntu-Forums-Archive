---
title: "Alt + F2 not working if gnome-panel isn't running"
date: 2009-11-13
forum: General Help
---

### Post by juanchito2006 on 2009-11-13
Hello, I've just found out that Alt + F2, for running commands, only works if gnome-panel is running. I've disabled gnome-panel in favour of Awn, so I wonder if is possible to have this "Run" window without having to run gnome-panel.

---

### Post by doas777 on 2009-11-13
not really. as I understand it, the panel applet is the thing listening for that hotkey, and the run application bar is also. 
how did you disable them? what happens if you leave the process running, and just delete the panels from your desktop?

---

### Post by VCoolio on 2009-11-13
Why not use kupfer / gnome-do / launchy if you need a run dialog?

---

### Post by juanchito2006 on 2009-11-16
> **doas777 said:**
> not really. as I understand it, the panel applet is the thing listening for that hotkey, and the run application bar is also. 
how did you disable them? what happens if you leave the process running, and just delete the panels from your desktop?

It's not that easy, when gnome-panel is running, you can't remove the last panel. I removed gnome-panel using the GConf editor, and disable it from running as the default panel.

> **VCoolio said:**
> Why not use kupfer / gnome-do / launchy if you need a run dialog?

I guess it's a good idea, though I expected Alt + F2 launching something independent from gnome-panel and being available as a stand-alone by default.

---

### Post by Perturbed Penguin on 2010-07-05
Yeah, I've run into this same problem. If someone has the physical command for that run dialog we could just make a new launcher for it and use that I would imagine but the location of the application does not appear to be documented anywhere. I guess I'll just use gnome-do for this purpose right now.

---

### Post by kerry_s on 2010-07-05
yeah i hate that to. lxde does the same thing.
1 of the things i do is set up a backup. i install "grun" to use.

---

