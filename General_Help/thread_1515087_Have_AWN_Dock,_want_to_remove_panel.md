---
title: "Have AWN Dock, want to remove panel"
date: 2010-06-21
forum: General Help
---

### Post by danbuter on 2010-06-21
I think all I have to do is disable gnome-panel somehow, but I wanted to check here first, so I don't screw up my computer. As it is, I have the dock working great. However, I can't just turn off the panel, which I currently have at the top of the screen. Any help would be appreciated.

---

### Post by TheNosh on 2010-06-21
right click the panel and select "delete this panel."

i'm not entirely sure how you get it back later if need be; good luck with that. ;)

---

### Post by warfacegod on 2010-06-21
Another option is to remove gnome-panel entirely.

---

### Post by danbuter on 2010-06-21
There is no option to delete the panel from right-click. I already tried that.

---

### Post by MooPi on 2010-06-21
```
sudo chmod -x /usr/bin/gnome-panel
```
reboot

---

### Post by warfacegod on 2010-06-21
Your menu doesn't give you this when you right click the panel?

---

### Post by danbuter on 2010-06-21
What exactly does that terminal command do?

And how can I reopen gnome panel later if necessary from terminal? 

Thanks!

---

### Post by danbuter on 2010-06-21
> **warfacegod said:**
> Your menu doesn't give you this when you right click the panel?

Nope. It did for the initial bottom panel (which I always delete).

---

### Post by warfacegod on 2010-06-21
You could remove everything from it, turn it transparent, and autohide it. That way it will still be there if you ever need it but it won't be in the way.

---

### Post by matt-fender on 2010-06-21
If you don't have the option to delete the panel, i would restore my panels to default. Can't remember the terminal codes, i think theres 3 of them? Then try deleting the panel again.

---

### Post by Ocxic on 2010-06-21
> **MooPi said:**
> ```
sudo chmod -x /usr/bin/gnome-panel
```reboot

The above command will prevent gnome-panel from loading. to get it back just:

sudo chmod +x /usr/bin/gnome-panel

Tip, you don't have to reboot, just logout and back in.

---

### Post by MooPi on 2010-06-21
> **danbuter said:**
> What exactly does that terminal command do?

And how can I reopen gnome panel later if necessary from terminal? 

Thanks!
```
sudo chmod +x /usr/bin/gnome-panel

```That will enable gnome panel, the previous command just makes the file un-executable, which is easily reverted as you can see. I have used this previously with great success.

---

