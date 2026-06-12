---
title: "Gnome Terminal Won't in 12.04"
date: 2012-04-28
forum: General Help
---

### Post by wmichaelb on 2012-04-28
On a new, clean install of 12.04, I cannot get Gnome Terminal to accept typed anything. Nothing shows up in the terminal screen itself: no shell prompt, no user name, no machine name. I uninstalled and reinstalled; no change.  Roxterm, xterm, and uxterm all  work; just not Terminal. What the bleep?....:-k

Is there something I did wrong in the install? Should I report this as a bug? Has anyone else seen this behavior? If it matters, I'm running an ASUS P5G41T-M mobo with an Intel E5700 and 8 GB of RAM, and 12.04 64-bit. Any and all suggestions are welcome, and thanks in advance.

---

### Post by Aiwa on 2012-04-28
Confirmed. I see exactly the same behavior after a release upgrade from 11.10 to 12.04.

I am running fluxbox in a VNC session. 64-bit Intel system.

---

### Post by w6fm on 2012-05-01
Same behavior here as well running a clean install of 12.04 64 bit on a Dell Latitude E5410 i5 Intel with 2gb ram.

---

### Post by jerrrys on 2012-05-01
Install lxterminal for now, it works.

---

### Post by Dennis N on 2012-05-02
Experienced a black screen only first time gnome terminal was started with no prompt or text visible and no text showed when entered. Turns out the text color is set to black as well.

**Solution**  

Edit > Profiles then either create a new one, or edit the default. In either case,  change the color scheme to something that is visible, such as built-in schemes: green on black.

If you create a new profile, be sure to set the new profile as the one to be used when launching terminal.

---

### Post by dennisonIT on 2012-07-04
I had this problem solved it by going to profile preferences/colours and un ticking the 'use colours from system theme' and hey presto all working again. Must have caused it when i was messing about with themes. The problem is irrelevant as I have now discovered Guake terminal......fantastic.

Cheers

Chris

---

### Post by cakmin on 2013-03-30
Thanks for sharing the solution everyone. I had the exactly the same problem and indeed, it was the colour preference of the terminal (black font on black background) that prevents us from seeing anything.

---

