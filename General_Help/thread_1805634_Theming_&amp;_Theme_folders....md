---
title: "Theming &amp; Theme folders..."
date: 2011-07-16
forum: General Help
---

### Post by UltraNEO* on 2011-07-16
Hi. I'm fairly new to Ubuntu... 
I've noticed there are many 'theme' folders tucked away under the filing system but they're application dependencies, so doesn't really concern me at this point. I like to know more information about those affect theming Gnome; essentially: 

**/usr/share/themes**/
**/home/***username***/.themes/** (hidden)

Could some care to explain what are the main differences? 

Where should themes really go? 
I've notice not all themes go in the same place, some are copied to both! Why?

And what permissions should the enclosed folders take on??

---

### Post by dino99 on 2011-07-16
mainly because of the designer(s), some are genuine ubuntu, and many others are untrusted. So you get good design and also some less.

---

### Post by CatKiller on 2011-07-16
> **UltraNEO* said:**
> 

**/usr/share/themes**/
**/home/***username***/.themes/** (hidden)

Could some care to explain what are the main differences? 



There's only one difference. Themes in /usr/share/themes are available for all users, which is why you need to be root to put anything there. Themes in ~/.themes are available for that user only, which is why you don't need any special permissions to put things there.

---

