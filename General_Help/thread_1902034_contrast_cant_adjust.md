---
title: "contrast cant adjust"
date: 2011-12-29
forum: General Help
---

### Post by divu on 2011-12-29
In my toshiba laptop l750, i installed edubuntu 11.10, in it I cant adjust brightness and contrast.....plse give me the solution.....

---

### Post by JC Cheloven on 2011-12-29
If normal methods don't work, you can always run this command. Open a terminal (ctrl-alt-t), and type ```
xrandr --output LVDS1 --brightness 0.6
```
Notes:
1) The "0.6" roughly means 60% (thus decreasing brightness). Change for something suitable for you (1.2 will increase brightness, for example).
2) I'm assuming here that you have a laptop. If that's not the case, that will not work. If so, please post back the outout of ```
xrandr
``` (whith no parameters).

---

