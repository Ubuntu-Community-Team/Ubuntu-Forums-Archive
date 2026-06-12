---
title: "Customizing keyboard layout a big"
date: 2010-08-14
forum: General Help
---

### Post by lamb123 on 2010-08-14
_Sry if wrong subforum_

[http://www.upload.ee/image/742292/Screenshot.png](http://www.upload.ee/image/742292/Screenshot.png)  <-- current layout (thinkpad T61)

I need to change only 4 key actions.

Right now when I press the colon key then " ; " symbol appears. But i need " ö " symbol
to appear instead of ; Basically i want to switch " ö " to appear as default and ; symbol with right-alt.

Right now i have to use right alt for " ö " symbol and thats really annoying. i need to change this for all 4 õüöä symbols.

Thanks.

---

### Post by simosx on 2010-08-15
> **lamb123 said:**
> _Sry if wrong subforum_

[http://www.upload.ee/image/742292/Screenshot.png](http://www.upload.ee/image/742292/Screenshot.png)  <-- current layout (thinkpad T61)

I need to change only 4 key actions.

Right now when I press the colon key then " ; " symbol appears. But i need " ö " symbol
to appear instead of ; Basically i want to switch " ö " to appear as default and ; symbol with right-alt.

Right now i have to use right alt for " ö " symbol and thats really annoying. i need to change this for all 4 õüöä symbols.

Thanks.

You need to change the variant from what you have in the screenshot to 
"Estonia - Eliminate dead keys".

You can verify visually that this variant prints the õüöä characters.

---

### Post by lamb123 on 2010-08-15
yes it does print üõöä characters but then inserting all other symbols get messed up, like " @ ' etc.

---

### Post by simosx on 2010-08-15
> **lamb123 said:**
> yes it does print üõöä characters but then inserting all other symbols get messed up, like " @ ' etc.

In that case then you can manually edit the keyboard layout so that it works as you expect it. The source of your problem above is that the 'no dead keys' variant follows the EU English layout instead of the US English (or the other way round).

To edit, 

sudo gedit /usr/share/X11/xkb/symbols/ee

In a nutshell, put the lines from the 'no dead keys' variant into the variant you prefer.

Btw, the default Estonian keyboard layout follow the official Estonian standards EVS8:1993 and EVS8:2000.

---

