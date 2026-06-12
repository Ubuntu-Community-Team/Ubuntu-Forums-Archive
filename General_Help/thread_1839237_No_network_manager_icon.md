---
title: "No network manager icon"
date: 2011-09-05
forum: General Help
---

### Post by jg2345 on 2011-09-05
Is there an easy way to fix this issue?

Along the top bar, there is no network manager icon. I cannot find it and I dont even know if it has network manager installed. The issue appeared on 10.10 and recently the gnome desktop of 11.04

---

### Post by gandaran on 2011-09-05
right click panel » add to panel » notification area

---

### Post by pratikk on 2011-09-05
And to start it manually, run nm-applet.

---

### Post by jg2345 on 2011-09-07
> **pratikk said:**
> And to start it manually, run nm-applet.
I tried that but it still does not show up. Im pretty sure it is installed but im not sure what is happening there:-k

---

### Post by pratikk on 2011-09-08
Looking back, it's not clear from your post if the machine has network access. In the meantime, here are some suggestions:

1. In the terminal, try which nm-applet. If it is installed, the system should reply /usr/bin/nm-applet. 
2. If it's missing, install it and add it to the panel as suggested by gandaran.
3. If it exists, has been added but is not showing, open terminal and run killall gnome-panel. The panel will die and reload, hopefully with the missing icon.
4. Slightly illogical but worth trying: in terminal, run "nm-applet &" without the quote marks.
5. Totally weird but it happens: Is this machine connected only by wireless, and does it have a physical wireless switch which may be off? I had this problem after an upgrade which toggled off my wireless. 

Trying to cover all bases because I don't know if you are connected or not. If these don't work, try googling this site for "nm-applet missing" or similar. A number of posts refer to a more serious issue, including instructions for setting up the network manually. 

Good luck

Pratik

---

