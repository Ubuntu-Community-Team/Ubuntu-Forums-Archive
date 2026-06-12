---
title: "Need to restore all panels, Ubuntu 9.04"
date: 2010-02-15
forum: General Help
---

### Post by Tayashlor on 2010-02-15
Hello all. 
I'm slightly new to using ubuntu and im having a problem that i cant solve and cant really find the right answers for.... 
here's the deal...
I deleted all my panels and have been using AWN. Well, Ive decided that I want my panels back. I can get the panels to run through terminal but if i restart, they disappear again. 

How do I permanently restore my panels?  I know that I had to turn off the values for Gnome-panel when deleting the last panel, and I just dont know where I went to do it because I was following instrustions from another thread. 

Any Help would be appreciated.

---

### Post by howefield on 2010-02-15
Try typing the following three commands into terminal.

```
gconftool-2 –-shutdown
```
```
rm -rf ~/.gconf/apps/panel
```
```
pkill gnome-panel
```

---

### Post by Tayashlor on 2010-02-15
All the commands went in but nothing happened. No response in terminal and No panels...

---

### Post by Tayashlor on 2010-02-15
Does anyone have any suggestions? I remember that when i deleted my last panel I had to change the values for gnome-panel. I cant remember what I had to do. 

Please anyone help.

---

### Post by howefield on 2010-02-15
Try running this, again in terminal

If you don't get panels after the first command, try running the second one in a run box, (press ALT+F2, and type) :

```
gconftool-2 --recursive-unset /apps/panel
```


```
killall gnome-panel && gnome-panel
```

---

### Post by Tayashlor on 2010-02-15
Neither code produced any results. 

If I use the code in terminal
sudo debconf gnome-panel

 Im then prompted for my password, After both Panels are restored but upon restart they disappear again.

*edit* I went back to terminal and there was this error

** Message: Could not connect to session manager: Could not get owner of name 'org.gnome.SessionManager': no such name

** (gnome-panel:32388): WARNING **: Could not connect to session manager: Could not get owner of name 'org.gnome.SessionManager': no such name

(gnome-panel:32388): libglade-WARNING **: Unexpected element <requires-version> inside <glade-interface>.

---

### Post by Tayashlor on 2010-02-15
can anyone help

---

### Post by MooPi on 2010-02-15
Just a shot in the dark but try ```
sudo chmod +x /usr/bin/gnome-panel
``` this is how I enable or disable gnome-panel.

---

### Post by Tayashlor on 2010-02-16
No results. It asked me for my password. and then it just opened another line. no panels.

---

### Post by pmlxuser on 2010-02-16
log out > log in

---

### Post by Primefalcon on 2010-02-16
your gnome panels?

```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```

then just log out and then in again and your panels should be back at default.

this deletes your gnome preferences so they go back to default when you log back in

---

### Post by Tayashlor on 2010-02-16
logged out, then logged back  in and still no panels.

---

### Post by Tayashlor on 2010-02-16
> **Primefalcon said:**
> your gnome panels?

```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```then just log out and then in again and your panels should be back at default.

this deletes your gnome preferences so they go back to default when you log back in


thank you, thank you, thank you!!! it worked. unfortunatly it deleted like my theme and everything, but thats okay. lol. i can always fix that later.

---

