---
title: "Broken NBR panel - everything is right justified"
date: 2009-08-25
forum: General Help
---

### Post by Anticontrame on 2009-08-25
Yesterday I plugged an external monitor into my netbook. Ever since, my panel has been broken.

I'm not sure how to describe it other than saying that everything is right justified, and that I can now drag panel items over to the area where the running applications are normally displayed. I've attached a screenshot:
[IMG]http://imgur.com/k9umR.jpg[/IMG]

My theme was also reset to the default, but I was able to get it back. I'm just not sure how to fix the panel. Rebooting does nothing. Does anyone know what to do?

Thanks!

---

### Post by tgeer43 on 2009-08-25
Not sure how to fix your existing panel but it might faster and easier to add a new panel and move your applets over to it then delete the old panel.

If you really want to try to troubleshoot the existing panel then you could run 'gksudo gconf-editor' and drill down to apps->panel->toplevels and muck around there a bit.

tgeer

---

### Post by Anticontrame on 2009-08-26
I'm not sure I can create a new one with the same functionality. In the netbook remix there are left-justified icons of programs running, right-justified traditional panel apps, and the remaining space in between is taken up by the scaled title bar of the program in focus.

The only item in toplevels is disable_movement, with a note that "This key has no schema."

---

### Post by blackened on 2009-08-26
You might doublecheck and make sure that you have unlocked all the items on your current panel as just one locked applet can prevent all the others from being movable, especially with the large titlebar applet in NBR.

Otherwise you should be able to rebuild it from scratch as has already been mentioned. All the applets should be in the "Add to Panel..." dialog.

---

### Post by Anticontrame on 2009-08-26
Aha! I hadn't realized I was looking for window-picker-applet. Making a new panel worked. Thanks guys!

---

