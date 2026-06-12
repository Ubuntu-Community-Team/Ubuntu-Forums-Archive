---
title: "Laptop Shortcuts (with Windows Key)"
date: 2009-09-22
forum: General Help
---

### Post by rDwyP44y on 2009-09-22
How do I get the “windows key” to work with my Ubuntu Keyboard Shortcuts? (*System>Preferences>Keyboard Shortcuts*)

When I try to assign the “windows key” it pops up as “Super L” and doesn’t allow me to assign another character

I would like to set the Ubuntu default Alt+F2 (Run application) to my keyboard “**Windows Key + R **“


***•	Also what’s the default Ubuntu shortcut to view the desktop??***

---

### Post by aloksethi on 2009-09-22
ctr+alt+d will take u to the desktop, works same as win+d

---

### Post by Rab22 on 2009-09-22
> **rDwyP44y said:**
> How do I get the &#8220;windows key&#8221; to work with my Ubuntu Keyboard Shortcuts? (*System>Preferences>Keyboard Shortcuts*)

When I try to assign the &#8220;windows key&#8221; it pops up as &#8220;Super L&#8221; and doesn&#8217;t allow me to assign another character

I would like to set the Ubuntu default Alt+F2 (Run application) to my keyboard &#8220;**Windows Key + R **&#8220;


***&#8226;	Also what&#8217;s the default Ubuntu shortcut to view the desktop??***

I have had difficultly in setting the Run Application dialog shortcut to Super+R as well. I receive the same "Super+L" combo when attempting, and then the "super" key by itself also becomes a shortcut key. 

CTRL + ALT + D is my "Show Desktop" key shortcut.  However, this maybe a Compiz-Fusion binding.

---

### Post by VCoolio on 2009-09-22
Give this a try: set "Super is mapped to the Win-keys" in System -> Preferences -> Keyboard -> Layouts -> Layout Options -> Alt/Win key behaviour.
Or open gconf-editor and edit the keybindings manually here:
-> apps -> metacity -> global_keybindings
-> apps -> metacity -> keybinding_commands

Use <mod4> to define the windows key.

---

### Post by pvfjr on 2009-09-28
> **VCoolio said:**
> Give this a try: set "Super is mapped to the Win-keys" in System -> Preferences -> Keyboard -> Layouts -> Layout Options -> Alt/Win key behaviour.
Or open gconf-editor and edit the keybindings manually here:
-> apps -> metacity -> global_keybindings
-> apps -> metacity -> keybinding_commands

Use <mod4> to define the windows key.
Thanks, just that one little setting really saved me a lot of frustration.  I can use the old Super R for running applications now, instead of being trapped in the inescapable magnifier mode.

---

### Post by pjalegria on 2009-10-01
[QUOTE]Use <mod4> to define the windows key./QUOTE]

What is this?

---

### Post by pjalegria on 2009-10-01
I can use <mod4> only...????

---

