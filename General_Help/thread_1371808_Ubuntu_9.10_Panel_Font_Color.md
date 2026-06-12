---
title: "Ubuntu 9.10 Panel Font Color"
date: 2010-01-03
forum: General Help
---

### Post by gos1 on 2010-01-03
Hi I am using a dark background in my panels and the system font color is dark too so I cannot see the text in panels. How can I change the color ? 
 
  I tried the gconf-editor. Changed the color value there and restarted the panel with 

   ```
killall gnome-panel
``` 

  Did not worked . And also I looked for the file gtkrc in my    ```
~/.themes/mytheme
```
 
  And could not find it. Is there any way to do this for 9.10 
 
  Thank You

---

### Post by ubudog on 2010-01-03
Right click on the panel, select "Properties", select the "Background" tab.  The settings should be there.

---

### Post by gos1 on 2010-01-04
Its not there . The color in that tab is the background color of the panel.

---

### Post by ubudog on 2010-01-04
Hmm. Maybe someone else can help.

---

### Post by stinkeye on 2010-01-04
gnome-color-chooser

---

### Post by gos1 on 2010-01-04
Works Great thank you .

---

