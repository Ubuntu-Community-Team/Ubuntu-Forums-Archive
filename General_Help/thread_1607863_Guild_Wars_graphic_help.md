---
title: "Guild Wars graphic help"
date: 2010-10-28
forum: General Help
---

### Post by thesimpsons98 on 2010-10-28
hi I have an ubuntu PC with 512 MB ram and an 3d graphic card that can normally support Guild Wars on windows xp. I installed the game with Wine an the game opens, I can see my character menu but the problem is none of the 3D graphic parts works, I just see a black screen.I even installed directX.
Please help.:confused:

---

### Post by WorMzy on 2010-10-28
Ubuntu isn't Windows, and as such will never be able to play games as well as Windows does, even through wine. That said, Guild Wars has received "platinum" status in [the WineHQ games database]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=9194"), so it should work quite well. One thing worth noting though is that apparently enabling the Pixel Shader in winecfg will cause the game to not render any 3D objects. So if you have Pixel Shader enabled, disable it.

---

### Post by thesimpsons98 on 2010-11-01
How can I close the pixel shader

---

### Post by WorMzy on 2010-11-01
You don't close it, you disable it. There should be an option in your winecfg graphics tab.

(Press Alt+F2, type "winecfg", click run, and the winecfg window should pop up. You may also have a menu item for it under Applications -> Wine)

---

