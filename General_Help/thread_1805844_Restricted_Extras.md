---
title: "Restricted Extras"
date: 2011-07-16
forum: General Help
---

### Post by nankura on 2011-07-16
Hey guys

i recently installed the restricted extras package but accidently didnt agree to the MS Fonts agreement, it says MS Fonts is installed

But the agreement window said if i dont accept, it wont work, and now i have no way to accept even in a reinstall of the MS Fonts

---

### Post by CatKiller on 2011-07-16
```
sudo dpkg-reconfigure ttf-mscorefonts-installer
```

might give you the opportunity to accept the agreement. You'll probably need to use Tab to select the Accept button.

---

