---
title: "Missing search box in Software Center"
date: 2011-11-09
forum: General Help
---

### Post by doriad on 2011-11-09
My Software Center is missing the search box in the top right: [http://daviddoria.com/Uploads/SoftwareCenter.png](http://daviddoria.com/Uploads/SoftwareCenter.png)

Is there a way to get it to be displayed?

Thanks,

David

---

### Post by doriad on 2011-11-11
Any thoughts on this?

---

### Post by raja.genupula on 2011-11-11
```
sudo apt-get install --reinstall software-center
```

I hope that will help you.

all the best,

---

### Post by doriad on 2011-11-11
Darn, nope, that didn't change anything :(

---

### Post by raja.genupula on 2011-11-11
> **doriad said:**
> Darn, nope, that didn't change anything :(

sudo apt-get remove --purge software-center
 and then install it again

---

### Post by domno25 on 2011-11-13
I am having the same problem.  I have tried the re-install and I tried uninstalling and reinstalling.  The search bar is still missing though.  I have also restarted my computer JIK but no dice.  Any one else have ideas how to fix this?

---

### Post by egkeat on 2011-11-20
I'm using 11.10, logging in with gnome shell desktop, and the software center search has always been missing. When I go back to Ubuntu, it's there again. Just not with gnome shell.

---

### Post by dshook4.6 on 2011-12-15
i also have the same problem using gnome, i can not even find software center in config editor

---

### Post by eric vandenburg on 2013-04-15
I have this problem on 12.10, but in my case at least, I found it was simply a layout bug with an easy workaround:   Make the software center's window frame a bit wider ( ~ 800 pixels )  and the search field will appear again.   If you close the window when it is wide enough to show the search field, then it will remember that width and show the search field correctly next time it is run.

---

### Post by lisati on 2013-04-16
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

