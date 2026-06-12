---
title: "Possible hack?"
date: 2006-03-18
forum: General Help
---

### Post by Blue1k on 2006-03-18
This is weird:

I installed a gdesklet from gdesklets.org. After the install, a runtime error appeared so I removed the package. Now my firefox launcher in the gdeskets Task Launcher won't work. I even tried launching it in /usr/bin/mozilla-firefox with no success. 

I then tried launching it from the menu and it worked fine. So I copied the command "firefox %u" that is in the menu and now the browser starts on arizona university page even when my start page is set to google. When I try to change it it reverts back to this webpage.

Not sure how to fix this, and I worry about a hack as I use this computer for banking.


Thanks!

---

### Post by byen on 2006-03-18
Just change the command to "firefox" instead of "firefox %u" in your gdesklets>edit starter menu for firefox. It should work!

PS- The reason why this happens is due to a known bug with dgesklets. 

Hope it helps..goodluck!

---

### Post by parktownprawn on 2006-03-18
As the previous post says this is a gdesklets bug.

If you enter "%u" into firefox's location bar the University of Arizona will come up. The University of Arizona is (for some unknown reason) the first google hit for "%u"

---

