---
title: "Wine messed up resolution"
date: 2010-10-13
forum: General Help
---

### Post by snowmanman on 2010-10-13
I ran wine to try to play Quake III Arena (which makes no sense because I already have open arena) and now the resolution is messed up. The screen is essentially split in two where the top half contains remnants of the screen before running wine and the bottom contains the top of the actual screen in ridiculously low resolution. The screen operates as if if was all the low resolution, but it is displayed lower than it actually is.

For example I have AWN and can click the menu in the lower left corner by moving my mouse to the area it would be and clicking, however, I cannot see it because I can only see the top half of the screen. 

I know this is confusing, but does anyone know how to return Ubuntu to it's former glory?

---

### Post by Refalm on 2010-10-13
It's an issue with AWN forcing to be on top.

You can try setting AWN to auto-hide, or shutting down AWN during a game.

---

### Post by snowmanman on 2010-10-14
No I don't think it was an AWN problem, It's tough to describe what happened, but I was able to run ```
gnome-session-save --silent
``` and that cleared it up. Normally when I shutdown I wasn't logged out and it saved the terrible setting. Doing this logged me out with the terminal and everything ended up working out.

---

