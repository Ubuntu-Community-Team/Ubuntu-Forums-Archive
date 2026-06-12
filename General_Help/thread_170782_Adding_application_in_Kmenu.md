---
title: "Adding application in Kmenu"
date: 2006-05-05
forum: General Help
---

### Post by wizzkid on 2006-05-05
Hi Guys,

I recently installed firestarter on kubuntu, its working when I start it by accessing sudo firestarter. I tried to add it using kmenu edit, on command i put firestarer, then when I tried to launch the program by clicking on menu, it says that i have no enought previllage to run the program, then I went back to kmenu edit, then i just add sudo in front of firestarter on command, but it doesnt work. Please help me with this.... 

Also, some of my installed program doesnt have an icon on kmenu, like opera browser, its probably the application is for gnome.

Thanks hope you guys could help me with his..

---

### Post by Parkotron on 2006-05-05
In KDE, instead of [FONT="Courier New"]**sudo**[/FONT], you should use [FONT="Courier New"]**kdesu**[/FONT] when starting graphical applications with root privileges. The GNOME equivalent is [FONT="Courier New"]**gksu**[/FONT]. So in your case, you want:```
kdesu firestarter
```

---

### Post by Al3xanR0 on 2006-05-05
[QUOTE=wizzkid]
Also, some of my installed program doesnt have an icon on kmenu, like opera browser, its probably the application is for gnome.

Thanks hope you guys could help me with his..[/QUOTE]

To add apps to the KDE menu right click on kmenu icon-> left click Menu Editor the rest is preety much self explanitory, but if you run into problems post again, please be vey specific.

---

