---
title: "Problem Running Conky in Lubuntu"
date: 2010-05-11
forum: General Help
---

### Post by LaneLester on 2010-05-11
It seems that Conky doesn't get along with PCManFM. I use EmelFM2 for file management, so I don't need PCManFM, and I could use feh for wallpapers. But if I disable pcmanfm, the logon screen is messed up.

Do you have a suggestion?

Lane

---

### Post by kdb424 on 2010-05-17
By has a problem, I'm assuming you mean it's flickering or updating wrong. I would suggest turning double buffering off if it is on, or vice versa to start.

---

### Post by LaneLester on 2010-05-17
> **kdb424 said:**
> By has a problem, I'm assuming you mean it's flickering or updating wrong. I would suggest turning double buffering off if it is on, or vice versa to start.

Yes, thanks, that helped, but it produced problems of its own. Further research (otherwise known as "googling") determined that pcmanfm is the problem, and the way to work around it is to use various conky settings which include "ownwindow yes." 

Conky is only satisfactory to me with "ownwindow no" so my solution has been to prevent the autostarting of pcmanfm in Lubuntu and Peppermint. I use emelfm2 for file management, so the loss of pcmanfm is insignificant to me.

Lane

---

