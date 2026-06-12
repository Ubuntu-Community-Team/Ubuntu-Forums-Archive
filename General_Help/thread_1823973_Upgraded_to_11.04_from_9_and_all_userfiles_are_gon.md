---
title: "Upgraded to 11.04 from 9 and all userfiles are gone"
date: 2011-08-12
forum: General Help
---

### Post by STCC on 2011-08-12
Hi, 

I just installed Ubuntu 11.04, i chose the option to upgrade from 9 (Jaunty) and keep all my user files. I am now in 11.04 and they're all missing, is there any way for me to get all my data back? Does Ubuntu store this data somewhere whilst upgrading? Before you say it i know i should have backed up all my stuff first, i am an idiot but if you can help i'd appreciate it. 

Thanks.

---

### Post by hyfanious on 2011-08-12
hi
where was ur home folder?
did u check that path(ur previous location)?
did u change ur username?
I came across a same problem when I change my username from "hyfanious" to "hyfanious-uv"
I checked my hidden folders and found them again ;)

---

### Post by Blasphemist on 2011-08-13
I agree with our Iranian friend. Making the installation choice that you say you made may have lost application settings but I doubt it would delete documents and such. I'd look within your directories and bet you'll find them in a subdirectory under /home.

---

### Post by STCC on 2011-08-13
Awesome, thanks for that, it's in the home folder under a different admin. Do you know where my desktop files would be?

---

### Post by hyfanious on 2011-08-13
I guess its depends on that u set a home path in the first installation or not
so for just this I set a separate partition (about 200 GiB) for my home folder
my desktop folder is keeps it that directory
but I guess if u didn't set that and use default setting the desktop folder must was stored in ur filesystem partition and I guess now u must lost it(I just guess, not sure)

use this command with one of ur filename that u know had it and see can it help u
```
locate filename
```

---

### Post by Blasphemist on 2011-08-13
I'm not sure what desktop files you are referring to. Files stored on the desktop are actually in /home/username/Desktop where username is the login.

---

### Post by STCC on 2011-08-13
I am blind lol. Thank you so much for your help. All the files are there.

---

### Post by hyfanious on 2011-08-13
marking solved threat as a SOLVED is a really good idea ;)

---

