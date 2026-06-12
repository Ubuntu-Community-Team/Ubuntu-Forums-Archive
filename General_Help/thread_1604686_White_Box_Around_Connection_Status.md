---
title: "White Box Around Connection Status"
date: 2010-10-24
forum: General Help
---

### Post by blindphaze on 2010-10-24
I have a new install of Ubuntu 10.10 (32bit) installed and I am noticing that on the top right corner where it shows the connection status, specifically the wired connection, it has a white box around it. 

I have tried changing the themes to something different but it is showing this on all the default themes I choose from. (Specifically Ambiance and New Wave).  I am sorry if there is already a thread about this but I really didn't even know how to begin with searching for this.

I am attaching a screen shot to show exactly what I am talking about.


I am also using the  Nvidia drivers (recommended version)  if this helps.

---

### Post by SavageWolf on 2010-10-24
Open /usr/share/icons/Humanity-Dark/status/22/gnome-netstatus-idle.svg and see if it has a white box around it.

(Go to Applications -> Graphics -> Image Viewer -> File -> Open -> Paste address into box)

EDIT: I assume you are using the default theme?

---

### Post by blindphaze on 2010-10-24
> **SavageWolf said:**
> Open /usr/share/icons/Humanity-Dark/status/22/gnome-netstatus-idle.svg and see if it has a white box around it.

(Go to Applications -> Graphics -> Image Viewer -> File -> Open -> Paste address into box)

EDIT: I assume you are using the default theme?


Yeah I am using the default theme at this time.  The actual picture itself does have checkerboard around it so I would say that it is safe to assume that it actually does not have white around it.

---

### Post by yetiman64 on 2010-10-24
The checkerboard indicates transparency usually, so the icon sounds OK.

It could be a problem with gnome panel. Try resetting with ALT + F2, type in "killall gnome-panel" (without the quotes) and click "Run".

 Don't "worry" about the command as the gnome panels automatically regenerate after dropping out for a second or two.

As as example of killall gnome-panel in use in my setup, I have attached a pic of the properties box of a launcher I have created on my top panel specifically to "fix" any glitches with the panels.

The command may be useful to reset your panels to their normal state.

---

### Post by blindphaze on 2010-10-24
> **yetiman64 said:**
> The checkerboard indicates transparency usually, so the icon sounds OK.

It could be a problem with gnome panel. Try resetting with ALT + F2, type in "killall gnome-panel" (without the quotes) and click "Run".

 Don't "worry" about the command as the gnome panels automatically regenerate after dropping out for a second or two.

As as example of killall gnome-panel in use in my setup, I have attached a pic of the properties box of a launcher I have created on my top panel specifically to "fix" any glitches with the panels.

The command may be useful to reset your panels to their normal state.

Thanks for the suggestion, this one didn't do the trick either it seems.  The system has been restarted a couple times since I first noticed this after the install.  Everything else with the system seems good, except this one glitch that I don't get.

---

### Post by blindphaze on 2010-10-24
Fixed it!  

What I did was just uninstalled the Nvidia driver, rebooted, reinstalled the *recommended* driver again, rebooted, and all is fine now :D

Thanks for the input though guys :)

---

