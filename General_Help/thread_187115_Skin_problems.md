---
title: "Skin problems"
date: 2006-06-02
forum: General Help
---

### Post by blackjack6.21.91 on 2006-06-02
I recently downloaded a skin (from gnome-look.org , i think), and it is absolutely beautiful.  That is, for most apps.  For some things the skin just doesn't seem to work.  Screenshots below of rythmbox (works) and synaptic (doesnt).  If my skin can't be applied to applications like synaptic, is there a way for those type of apps to perhaps look a little more like they do under clearlooks?

thanks

---

### Post by nastya on 2006-06-02
If I remember correctly, Synaptic is gtk, while rhythmbox is gtk2. Is the skin that you installed just for gtk2 or did you install a skin for the other as well?

---

### Post by givré on 2006-06-02
[QUOTE=nastya]If I remember correctly, Synaptic is gtk, while rhythmbox is gtk2. Is the skin that you installed just for gtk2 or did you install a skin for the other as well?[/QUOTE]
Not really, synaptic and rhythmbox are both gtk2, but you will run one as root and the other one as a simple user, that's the difference. Try to run nautilus as root and you will see the difference (gksu nautilus)

Let us know how you install this theme, you will probably have to do the same for the root user (but there is probably a better soluce )

---

### Post by mcduck on 2006-06-02
[QUOTE=givré]Not really, synaptic and rhythmbox are both gtk2, but you will run one as root and the other one as a simple user, that's the difference. Try to run nautilus as root and you will see the difference (gksu nautilus)

Let us know how you install this theme, you will probably have to do the same for the root user (but there is probably a better soluce )[/QUOTE]
Here's a smooth solution to set root to use same theme that you use.
Open a terminal, and run these commands:
```
sudo ln -s ~/.themes /root/.themes
sudo ln -s ~/.icons /root/.icons
```
(That makes symbolic links from your themes and icons folders to root user's home)

---

### Post by lapsey on 2006-06-02
worked perfectly, thanks!

---

### Post by blackjack6.21.91 on 2006-06-02
thanks alot!  you pimped my desktop!

---

### Post by mcduck on 2006-06-03
no problem. :)

If you want root apps to use same fonts too, you can also do this:
```
sudo ln -s ~/.fonts /root/.fonts
```

---

