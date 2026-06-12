---
title: "Gnome Shell 3.4 and shortcuts"
date: 2012-05-29
forum: General Help
---

### Post by balasankarc on 2012-05-29
Hi all,
I use ubuntu 12.04 precise pangolin and I've updated to GNOME shell 3.4. When i was using earlier version, i could drag apps from sidebar to desktop, thereby make a shortcut of them in desktop.
but now i cannot drag programs to desktop coz there is no sidebar... 
pls tell me how to create shortcuts of programs in desktop.

Balasankar C

---

### Post by Frogs Hair on 2012-05-29
Could you post a screen shot ? I have a favorites bar in Gnome 3.4 as was in 3.2. Make sure you are logged into Gnome and not Gnome Classic. If you are logged into the Gnome Shell use Alt+F2 and reset the shell with the following. ```
r
```

---

### Post by balasankarc on 2012-05-29
sorry, but i dnt know what to post as screenshot...i can't drag and drop icons from favorites bar so as to make shortcuts in the desktop... how can i do it is my question...

---

### Post by kurt18947 on 2012-05-29
I've never been able to create desktop shortcuts in shell. Unity yes, but not shell.  However, this will work.  You do have to know the command to launch the application, e.g. 'firefox' to launch firefox.  

In a terminal type
```
gnome-desktop-item-edit ~/Desktop/ --create-new
```

This will open a 'create launcher' window.  Fill in the blanks and you should be set.

---

### Post by Frogs Hair on 2012-05-29
This is what was written so I am confused . Do you have a favorites/ side bar or not.> but now i cannot drag programs to desktop coz there is no sidebar...

---

### Post by balasankarc on 2012-05-29
> **Frogs Hair said:**
> This is what was written so I am confused . Do you have a favorites/ side bar or not.

there is a favorites bar, i agree... but its different frm unity sidebar... thts wot i said...

---

### Post by balasankarc on 2012-05-29
> **kurt18947 said:**
> I've never been able to create desktop shortcuts in shell. Unity yes, but not shell.  However, this will work.  You do have to know the command to launch the application, e.g. 'firefox' to launch firefox.  

In a terminal type
```
gnome-desktop-item-edit ~/Desktop/ --create-new
```

This will open a 'create launcher' window.  Fill in the blanks and you should be set.

sorry, but as i'm a newbie, i am just familiarizing with commands... can u pls tell me how can i get commands of various programs... for eg. i want to create a launcher for the torrent client Vuze (Azureus)... pls tell me how...

---

### Post by kurt18947 on 2012-05-29
> **balasankarc said:**
> sorry, but as i'm a newbie, i am just familiarizing with commands... can u pls tell me how can i get commands of various programs... for eg. i want to create a launcher for the torrent client Vuze (Azureus)... pls tell me how...

Often it's the name of the application typed in a terminal.  There is one thing you could try.  I have Synaptic installed which is a package manager sort of like Ubuntu Software Center.  I can open it, type in the name of the application I want to launch in the quick filter bar.  For example, transmission is the default torrent program.  If I open a terminal and type 'transmission' nothing is found.  If I open synaptic and type 'transmission' in the quick filter window, one of the first results is 'transmission-gtk'  When I type that in a terminal,  Transmission will launch.  There may be better methods and perhaps others will suggest them.   I hope this is of some help.

---

### Post by balasankarc on 2012-05-29
> **kurt18947 said:**
> Often it's the name of the application typed in a terminal.  There is one thing you could try.  I have Synaptic installed which is a package manager sort of like Ubuntu Software Center.  I can open it, type in the name of the application I want to launch in the quick filter bar.  For example, transmission is the default torrent program.  If I open a terminal and type 'transmission' nothing is found.  If I open synaptic and type 'transmission' in the quick filter window, one of the first results is 'transmission-gtk'  When I type that in a terminal,  Transmission will launch.  There may be better methods and perhaps others will suggest them.   I hope this is of some help.

Thanks buddy...

---

### Post by minemax on 2013-05-26
> **kurt18947 said:**
> ...

In a terminal type
```
gnome-desktop-item-edit ~/Desktop/ --create-new
```

This will open a 'create launcher' window.  Fill in the blanks and you should be set.

It worked! Thank you very much.

---

