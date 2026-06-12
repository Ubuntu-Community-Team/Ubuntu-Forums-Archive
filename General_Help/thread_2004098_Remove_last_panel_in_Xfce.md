---
title: "Remove last panel in Xfce?"
date: 2012-06-15
forum: General Help
---

### Post by Rytron on 2012-06-15
Hi.

How could I hide/remove the last panel in Xfce? This is how it is done in GNOME2: [http://glx-dock.org/ww_page.php?p=Remove%20the%20last%20Gnome%20Panel&lang=en](http://glx-dock.org/ww_page.php?p=Remove%20the%20last%20Gnome%20Panel&lang=en)

---

### Post by Linux_junkie on 2012-06-15
Can you please explain what you mean by "last panel"?  You can hide or even remove all panels from XFCE if you wish,

Simply right-click on the panel you want to remove then select 'remove'.  Or if you want to auto-hide the panel simply goto panel properties and select option to auto-hide.

Is that what you mean?

---

### Post by Rytron on 2012-06-15
> **Linux_junkie said:**
> Can you please explain what you mean by "last panel"?  You can hide or even remove all panels from XFCE if you wish,

Simply right-click on the panel you want to remove then select 'remove'.  Or if you want to auto-hide the panel simply goto panel properties and select option to auto-hide.

Is that what you mean?

I don't refer to auto-hiding but rather Hide/Remove completely. So if I was to use a dock, the Xfce panel would not be required.

I tried right-click on the panel to remove then select 'remove' but that only remove items from the panel.

---

### Post by Linux_junkie on 2012-06-15
Right click on panel select 'Panel' then 'Panel Properties then click on the big red X button.

---

### Post by Rytron on 2012-06-15
> **Linux_junkie said:**
> Right click on panel select 'Panel' then 'Panel Properties then click on the big red X button.

It is greyed out if you have only 1 panel left.

---

### Post by Linux_junkie on 2012-06-15
Sorry I just assumed you could get rid of all panels.  Having looked through the XFCE website it's not possible.  I suppose the work around is to set the panel to auto-hide.

---

### Post by Rytron on 2012-06-15
> **Linux_junkie said:**
> Sorry I just assumed you could get rid of all panels.  Having looked through the XFCE website it's not possible.  I suppose the work around is to set the panel to auto-hide.

No problem.

I did try the last solution here from but no joy. [http://unix.stackexchange.com/questions/38048/how-to-remove-all-the-panels-in-xfce](http://unix.stackexchange.com/questions/38048/how-to-remove-all-the-panels-in-xfce) You can't not delete all panels, the right way of doing this is disable it from autostart...

---

### Post by Linux_junkie on 2012-06-15
Maybe a solution.

menu -> Settings -> Settings Editor -> XFCE-Panel

Change panels to 0 (zero) then save.

Reboot.  

Has panels been removed?

---

### Post by Rytron on 2012-06-15
> **Linux_junkie said:**
> Maybe a solution.

menu -> Settings -> Settings Editor -> XFCE-Panel

Change panels to 0 (zero) then save.

Reboot.  

Has panels been removed?

I reckon you are close but no luck.

---

### Post by Linux_junkie on 2012-06-15
Try removing XFCE-Panel package from system.

---

### Post by Rytron on 2012-06-15
> **Linux_junkie said:**
> Try removing XFCE-Panel package from system.

There is no package titled 'XFCE-Panel'. It would proably be impossible to remove just the panel without breaking the system.

---

### Post by Zvlwab on 2012-06-15
```
sudo apt-get purge xfce-panel
```

---

### Post by Rytron on 2012-06-15
> **Zvlwab said:**
> ```
sudo apt-get purge xfce-panel
```

```
E: Unable to locate package xfce-panel
```

---

### Post by Zvlwab on 2012-06-15
> **Rytron said:**
> ```
E: Unable to locate package xfce-panel
```

oops, I meant:
```
sudo apt-get purge xfce4-panel
```

All depending packages that will be removed, are just panel plugins.

---

### Post by Rytron on 2012-06-15
> **Zvlwab said:**
> oops, I meant:
```
sudo apt-get purge xfce4-panel
```

All depending packages that will be removed, are just panel plugins.

Hi Zvlwab. You did it! :)

---

### Post by brainwash on 2012-06-15
Navigate to Settings Manager > Session and Startup > Session, kill the xfce4-panel process and save the session state.

---

### Post by Rytron on 2012-06-15
> **brainwash said:**
> Navigate to Settings Manager > Session and Startup > Session, kill the xfce4-panel process and save the session state.

Thank you sir. Works like a charm.

To re-add it, just run xfce4-panel in terminal and save session.

---

### Post by Jose Catre-Vandis on 2012-06-15
Great thread, (OP prepared to try anything ;)), great problem solving, great support, great solution :)

---

