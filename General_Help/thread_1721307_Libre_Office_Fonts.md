---
title: "Libre Office Fonts?"
date: 2011-04-04
forum: General Help
---

### Post by Roasted on 2011-04-04
Is it possible to "extract" the Libre Office set of fonts and install them on MS Office? I ask this because we are integrating Libre Office heavily but since we have some Office 07 licenses that are essentially paid for, we're trying to utilize those licenses in some areas for a while yet, but there are some font incompatibilities when users make documents with certain fonts on Libre and then try to open them on MS Office 07.

---

### Post by falko on 2011-04-04
Basically yes as TTF fonts are just simple files that you can copy over to other systems.

---

### Post by Roasted on 2011-04-04
> **falko said:**
> Basically yes as TTF fonts are just simple files that you can copy over to other systems.

Where are fonts for Libre stored then? I would like to copy them to our remaining MS Office systems.

---

### Post by coffeecat on 2011-04-04
EDIT: sorry, misunderstood your post first time around.

I believe Libre Office simply uses the fonts installed in the system. In Ubuntu, you will be able to find the *ttf files in various folders in /usr/share/fonts/truetype.

If any fonts have been installed locally for a user account, they will be in the hidden folder /home/username/.fonts.

---

### Post by ~Plue on 2011-04-04
> **Roasted said:**
> Where are fonts for Libre stored then? I would like to copy them to our remaining MS Office systems.
doesn't it just use the system fonts?
see /usr/share/fonts/  and  /home/<usrname>/.fonts/

---

### Post by scouser73 on 2011-04-04
They can be found in **/usr/share/fonts/truetype/ttf-liberation/truetype** and **/usr/share/fonts/truetype/ttf-liberation/type1**

---

