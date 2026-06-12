---
title: "Resize terminal window when launched with Ctrl+Alt+T"
date: 2011-12-12
forum: General Help
---

### Post by AcidHawk on 2011-12-12
Hi,

I can press Ctrl+Alt+T to launch a terminal window.  I can also press Super+A ->term and click on terminal, both of these launch the gnome terminal (AFAIK)

So here's the thing - when I created a launcher previously I was able to set the geometry so I would always launch a terminal window using the same (bigger than default) window size.

I want to change the default size of the terminal window that gets launched when I press Ctrl+Alt+T - etc.

Any Ideas ... I can't right-click on the launcher after pressing Super+A as this just launches the terminal window using the default geometry ....

---

### Post by AcidHawk on 2011-12-12
some progress...

I have now tried to edit the file /usr/share/applications/gnome-terminal.desktop

I have updated the Exec=gnome-terminal line to look as follows  Exec=gnome-terminal --geometry=80x40

but it is not working ...

although as I am typing this I had a thought that I should restart unity... I'll restart and update any progress.

Regards
Acidhawk

---

### Post by AcidHawk on 2011-12-12
Nope ...

unity --replace did not work...

so I guess the question is - what launcher is CTRL+ALT+T running ..?

---

### Post by AcidHawk on 2011-12-12
Interesting to note though .... 

When I press Super+A and type terminal ... and click that shortcut the size has been changed... it's only CTRL+ALT+T that is still not working

---

### Post by pastalavista on 2011-12-12
To change the size of the gnome-terminal window, right-click in the window and select profiles/profile preferences. In the window that appears, click the box at the bottom of the first tab that says 'use custom default terminal size' and set it at whatever size you want.

---

### Post by AcidHawk on 2011-12-12
Ok got it ...

Super-A look for config -> click on CompizConfig Settings Manager

Then under the General tab under the Gnome Compatibility there is a Commands tab.

I noticed a Terminal command line input field which I changed from gnome-terminal to gnome-terminal --geometry=120x50

now when I press CTRL+ALT+T I get the terminal window in the size I want... ;)

---

### Post by AcidHawk on 2011-12-12
> **pastalavista said:**
> To change the size of the gnome-terminal window, right-click in the window and select profiles/profile preferences. In the window that appears, click the box at the bottom of the first tab that says 'use custom default terminal size' and set it at whatever size you want.

Ooohh.... I didn't even know this setting existed .... this was far easier than my way.... 

Thank you

---

