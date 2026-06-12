---
title: "cant login-authentification failure"
date: 2011-11-03
forum: General Help
---

### Post by CleveRuse on 2011-11-03
Just fresh-installed 10.04 and I can't even login. So i went into the BIOS and set my system pswd and then reset my user pswd, both to '3333'. Now when I enter the BIOS I must enter the pswd, then when i want to change either of my pswds, I need to also enter the correct one ...and its accepted every time. So despite the fact that there's no freakin way I screwed up '3333' (twice) during setup, I know for a fact its the correct pswd now! It works everywhere else ...WTF???? I've even tried different/longer pswds. Nothing works! 

Also tried login by 'ctrl+alt+f6'!

Please help! This is ridiculous:( ...and i really can't see how this could possibly be my mistake! ...but I suppose it wouldn't be the first time;)

---

### Post by LowSky on 2011-11-03
BIOS doesn't have anything to do with the Operating System. Using or changing the BIOS password will only effect the BIOS.

From what you are saying I have no idea how your system's password has changed, unless you did it from Ubuntu recovery function. but I don't know for sure.

---

### Post by pavi_elex on 2011-11-04
change your password of root account.
1. Press esc during booting, the recovery options will be shown.
2. Press e on default option that is first option of the list.
3. Select kernel option and press e to switch into edit mode
4. delete the last words "ro quite splash" and write "rw init=/bin/bash" (without quotation)
5. Press enter then b for booting
6. now type "passwd root" for reset root password and "passwd user" for reset user password. (without quotation)

---

