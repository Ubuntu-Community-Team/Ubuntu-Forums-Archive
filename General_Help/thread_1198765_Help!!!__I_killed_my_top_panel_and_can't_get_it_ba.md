---
title: "Help!!!  I killed my top panel and can't get it back!"
date: 2009-06-27
forum: General Help
---

### Post by Zorgoth on 2009-06-27
I just killed my top panel by accident and although I know how to edit panels, I can't seem to find some of the normal things that go there.  There is a battery charge monitor, but it doesn't look like the normal one, a "notification area" which mostly looks like my task list but for some reason doesn't have very many things on it; in particular it doesn't have the thing that tells me about my wireless and the thing that tells me about my ethernet.

Is there a way to get back my default panel, and if not where are all the things that go on it?

---

### Post by ad_267 on 2009-06-27
The task list will show those icons if you log out and log back in again. I don't think there's a way to revert your panel configuration back to the default unless you find out where the configuration files are stored and delete them.

---

### Post by synapsys on 2009-06-27
All the default tasks are listed in the 'add to panel' list. 
I know this because I recently nuked my panel and 
was able to restore it by right clicking and selecting 
add to panel.

---

### Post by drs305 on 2009-06-27
You can run this to refresh the panels to see what returns:
```

killall gnome-panel

```

To save your current panel settings (creates a file on your Desktop called *panels*):
```
gconftool-2 --dump /apps/panel > **~/Desktop/panels**
```
To restore your saved panel settings (from file $HOME/Desktop/panels):
```
gconftool-2 --load **~/Desktop/panels** && killall gnome-panel
```

To restore the original top & bottom default panels (you will lose any customizations you have made):
```
gconftool-2 --recursive-unset /apps/panel && gnome-panel &
```

---

### Post by philcamlin on 2009-06-27
> **drs305 said:**
> You can run this to refresh the panels to see what returns:
```

killall gnome-panel

```To save your current panel settings (creates a file on your Desktop called *panels*):
```
gconftool-2 --dump /apps/panel > **~/Desktop/panels**
```To restore your saved panel settings (from file $HOME/Desktop/panels):
```
gconftool-2 --load **~/Desktop/panels** && killall gnome-panel
```To restore the original top & bottom default panels (you will lose any customizations you have made):
```
gconftool-2 --recursive-unset /apps/panel && gnome-panel &
```

thanks that helped me :popcorn:

---

### Post by sigurnjak on 2009-06-28
I know it is little late  , but i did similar thing few times and i found this tip to reset my desktop when gconf did not work 

rm -rf .gnome .gnome2 .gconf .gconfd .metacity

and reboot. 

Hopefully it helps someone !

---

