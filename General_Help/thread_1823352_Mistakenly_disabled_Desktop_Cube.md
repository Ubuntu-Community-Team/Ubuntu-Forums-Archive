---
title: "Mistakenly disabled Desktop Cube"
date: 2011-08-11
forum: General Help
---

### Post by princeofnam on 2011-08-11
I'm running 11.04 with Unity and enabled Desktop Cube in Compiz Settings Manager.  I ended up disabling services, i think "largedesktop" and enabling others like OpenGL and composite.  Anyway, unity no longer works including the bar above and the icons to the left.  Any idea how I can fix this?

---

### Post by garvinrick4 on 2011-08-12
```
unity --reset
```
Below reset compiz settings
```
gconftool-2 --recursive-unset /apps/compiz 
```

---

### Post by apiwarski on 2011-08-12
i just recently had that happen to me and i did a fresh reinstall.... i am a new user to linux so I too was unsure. with this you were unable to run terminal in  any way. 

the hot keys and upper task bar were/are gone, same with the "quick launch" if you will ( forgive me i was a windows user) on the left was not there as well..... all i had was my 2 desktop icons on my attached drives mounted. i could not run anything other than that.!!! 

can you explain this to me since i will be putting natty on my net book in a few days????

thanks

---

