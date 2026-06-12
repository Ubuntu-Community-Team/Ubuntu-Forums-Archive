---
title: "How to Start Programs automatically in a non-gnome environment?"
date: 2011-10-07
forum: General Help
---

### Post by bartmc on 2011-10-07
I'm running a very minimal window manager (either sawfish,lwm or matchbox) and trying to launch a program when the WM starts. I'm not launching any sort of toolbar,panel etc... just a blank desktop and I need to run a GUI program. I have the system setup to auto-login if that makes any difference. This is for a kiosk/POS type of system where I really just need my application to lanuch and nothing else.

---

### Post by blueridgedog on 2011-10-07
> **bartmc said:**
> sawfish,lwm or matchbox

They each will have a different answer.  Which one?

---

### Post by bartmc on 2011-10-07
matchbox i 99% ruled out because it launches the panel and looks more like something for a PDA. LWM i worked with a day or two but it seems to have zero options. So lets call it sawfish.

---

### Post by bartmc on 2011-10-07
After some intense googling I found that I needed to create a file

~/.sawfish/rc

and add

    (add-hook 'after-initialization-hook 
        (unless batch-mode (system "xterm &")) 
        t) 

to it.

---

