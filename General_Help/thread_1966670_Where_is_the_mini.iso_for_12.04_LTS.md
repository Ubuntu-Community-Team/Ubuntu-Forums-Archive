---
title: "Where is the mini.iso for 12.04 LTS?"
date: 2012-04-27
forum: General Help
---

### Post by cheway on 2012-04-27
I always use the mini.iso for my installations - does anybody know where the 12.04 LTS version is please? 

It's not here [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Cheers,
Matt.

---

### Post by JC Cheloven on 2012-04-27
Hi, I don't find it either, but you can obtain an equivalent result using the [alternate install CD]("http://www.ubuntu.com/download/desktop/alternative-downloads"), and choosing to install a text-console system (with no GUI).

Hope this helps 
JC

EDIT: Oops I'm afraid you meant a different thing, sorry. I understood you intended to start from a minimal install to build a systen with just the apps you want (I do that often). Anyway, perhaps you want to try that path.

---

### Post by Cheesemill on 2012-04-27
[http://cdimage.ubuntu.com/netboot/precise/](http://cdimage.ubuntu.com/netboot/precise/)

---

### Post by cheway on 2012-04-27
Thanks JC, that's good to know. Is it EXACTLY the same for all intents and purposes? Still, I like to use the mini.iso as it fits on a small CD.

Cheesemill, that mini.iso is dated "23-Apr-2012 20:05", which was a few days before the release yesterday (26th April). Does that mean it's a beta or something?

Cheers guys,
Matt.

---

### Post by Cheesemill on 2012-04-27
> **cheway said:**
> Thanks JC, that's good to know. Is it EXACTLY the same for all intents and purposes? Still, I like to use the mini.iso as it fits on a small CD.

Cheesemill, that mini.iso is dated "23-Apr-2012 20:05", which was a few days before the release yesterday (26th April). Does that mean it's a beta or something?

Cheers guys,
Matt.

No, it's final.
Nothing on it changed or had updates in the last few days.

---

### Post by cheway on 2012-04-27
Sweet, thanks.

---

### Post by JC Cheloven on 2012-04-28
> **cheway said:**
> Thanks JC, that's good to know. Is it EXACTLY the same for all intents and purposes? Still, I like to use the mini.iso as it fits on a small CD.
Hi, 
The result should be pretty equivalent IF YOU WANT SO. In fact, if you click in the "installation guide" link in the page suggested by Cheesemill, you'll get to the instalation guide for the alternate cd.

The main difference is that with the mini iso -netboot-, packages are downloaded automatically (if you're connected to the internet). On the other hand, if you install a text console system, you have to actively issue a command like ```
sudo apt-get install ubuntu-desktop
```
to install the graphical ubuntu desktop and all its applications.

Nevertheless, the method is probably more useful when you want to choose your own set of applications instead of the default one provided (decided) by the ubuntu developers. For example, I use something similar to LUbuntu, but I prefer firefox and evolution over chromium and sylpheed, so I install first a cli systen, then some lxde-related packages and the LUbuntu artwork (this gives me the basic graphical system), and then I install the apps I like. 

Hope to have made it clearer
JC

---

### Post by NKJensen on 2013-03-10
> **cheway said:**
> I always use the mini.iso for my installations - does anybody know where the 12.04 LTS version ...
It's listed now, here: [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD) - all of the mini.iso images are there

---

