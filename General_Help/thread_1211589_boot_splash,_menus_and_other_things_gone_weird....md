---
title: "boot splash, menus and other things gone weird..."
date: 2009-07-12
forum: General Help
---

### Post by kforum on 2009-07-12
ok first thing of strange that i noticed lately and got no idea what to do about it is:

i deleted my last partition(that had windows:guitar:) and integrated it into my ubu one(that was right before it), ok after that i fixed fstab, grub and everything was ok, great...

however the little boot splash loading screen went away,
now what i see is the loading bar going back and forth once or twice, then when it actually starts to load stuff, it switches to terminal interface and i see everything o.o!(not that i mind, but it would be good to know what caused this)


second thing, when i uninstalled a certain app from wine it kept the menus of that certain app there. then when i removed wine, i simply deleted the menu altogether...
however after re-installing wine later on, it doesnt re-create the menus anymore, in fact its quite weird because the menus ARE created in the /etc/xdg/..... folder but they never show up on the gnome menu panel.
(and no its not 'hidden' or anything...)

these are the latest weirdos that only ubu gives...:roll: however i havent been able to fix it this time.


thanks for any suggestion,

cheers.

---

### Post by VCoolio on 2009-07-12
```
sudo dpkg-reconfigure linux-image-`uname -r`
```

This may fix your usplash. Just reconfiguring, nothing can be broken, give it a shot.

---

### Post by kforum on 2009-07-13
yeah, that didn't do much.
thanks for the suggestion though, i was looking for a debian specific solution actually(like the one you suggested).

but this wasn't it... its weird really everything in the menu.lst is fine and dandy. i dont really get whats going on. maybe i should delete the img and 'reconfigure'?

dont know, atm im still not sure what to do.

again,
thanks for any response.

---

### Post by kforum on 2009-07-19
no more ideas, anyone?

---

### Post by kforum on 2009-09-01
still havent solved teh bootsplash... is ti something that ubu does to the kernel when it installs?

cause my swap partition id changed since then(i did change it in fstab too but...).

---

### Post by kforum on 2009-09-02
i fixed this by installing 'startUp-manager" and doing things 'the gui way', im still not sure what it fixed, but it fixed it ^^.

cheers

---

### Post by kforum on 2009-09-02
also, about my other issue... i found this:
i resolved the problem here is how to fix it

Code:

cd /home/user/.config/menus/
rm applications.menu


replace user by ur ubuntu username

-------------
truth is that, just go to that folder and do what you need to get the menu to look as needed. 

cheers

---

