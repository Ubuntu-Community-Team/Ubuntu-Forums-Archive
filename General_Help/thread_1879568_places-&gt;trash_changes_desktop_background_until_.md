---
title: "places-&gt;trash changes desktop background until logout"
date: 2011-11-11
forum: General Help
---

### Post by linuxcss on 2011-11-11
xubuntu 11.10

I have places added to panel and if you select trash location (sometimes by accident) it changes the background on desktop to dark blue and then trying to change desktop background properties does not invoke ... only way to get desktop background restored is to logout 

anybody see this yet? And if so is there a workaround without logging out to restore the desktop background with icons??

---

### Post by linuxcss on 2011-11-11
i had installed nautilus and I see when trash is select it invokes nautilus for some reason .... if I kill that process can get desktop restored without log out ... anyway to stop trash when opened via places to not use nautilus (without uninstalling nautilus)????

---

### Post by Toz on 2011-11-12
In Settings Manager -> Preferred Applications -> Utilities Tab, do you have Thunar set as your default File Manager?

---

### Post by linuxcss on 2011-11-12
yes  thunar is set as default ... do not know why it starts the nautilus process for only trash the other icons on places work

---

### Post by Toz on 2011-11-12
What does the following return:
```
gconftool-2 --dump /desktop/gnome/url-handlers/trash/command
```

If it references nautilus, you can try:
```
gconftool-2 --set --type=string /desktop/gnome/url-handlers/trash/command 'thunar %s'
```

---

