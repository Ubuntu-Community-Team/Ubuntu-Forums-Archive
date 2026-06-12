---
title: "Home (~/) is now my desktop, how do I unassociate?"
date: 2010-02-15
forum: General Help
---

### Post by petaloid on 2010-02-15
I was moving some files around and for some reason after I restarted my Home folder has become the desktop.

I realised this was because I moved "~/Desktop" somewhere else" and now it was seeing "~" as my desktop.

I moved the Desktop dir back to where it was, inside ~ but I can't get ubuntu to stop seeing ~ as my desktop. I want it to display the contents of ~/Desktop on the desktop, but it keeps displaying ~ instead on the desktop.

Thanks.

---

### Post by ElSlunko on 2010-02-15
Perhaps doing the inverse of this might work :

[http://www.simplehelp.net/2008/08/26/how-to-use-your-home-folder-as-your-desktop-in-ubuntu/](http://www.simplehelp.net/2008/08/26/how-to-use-your-home-folder-as-your-desktop-in-ubuntu/)

---

### Post by jken146 on 2010-02-15
Also check ~/.config/userdirs.dirs

---

### Post by petaloid on 2010-02-15
Thanks, jken146 and ElSunko. I tried editing the userdirs.dir file and it fixed it.

---

