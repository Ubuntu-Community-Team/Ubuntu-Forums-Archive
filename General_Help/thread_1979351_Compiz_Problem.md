---
title: "Compiz Problem"
date: 2012-05-13
forum: General Help
---

### Post by bOgNeR17 on 2012-05-13
I have just installed and changed my Lubuntu system to use Compiz. Now for some reason the menu windows have no title or exit/minimize/maximize buttons. How do I remove Compiz and return to what I was using?

---

### Post by pqwoerituytrueiwoq on 2012-05-13
you have to open ccsm and enable the window decorations

---

### Post by bOgNeR17 on 2012-05-13
Could you please tell me how enable it?

---

### Post by zombifier25 on 2012-05-13
Install ccsm first:
```
sudo apt-get install compizconfig-settings-manager
```
Then open CompizConfig Settings Manager, enable "Windows Decoration".
P.S. Don't use Compiz before making sure all essential plugins is enabled via ccsm.

---

### Post by bOgNeR17 on 2012-05-13
I don't want to use Compiz anymore I want to return to the Lubuntu default windows manager and remove Compiz.

---

### Post by JC Cheloven on 2012-05-13
> **bOgNeR17 said:**
> I don't want to use Compiz anymore I want to return to the Lubuntu default windows manager and remove Compiz.

That's wise, IMO. Using compiz under lubuntu/lxde is an oximoron.

It's difficult to guess in which state is your computer right now(*), but I think opening synaptic, searching for compiz, and unisntalling everything compiz-related from there, should suffice. 

[INDENT](*) I'm thinking of, perhaps, some needed lxde package being uninstalled by you in the process. Don't worry, if your desktop don't show up after uninstalling compiz, you can go to a system terminal (Ctrl-Alt-F1) and do this addmitedly oversized action:
```
sudo apt-get install lubuntu-desktop
```[/INDENT]

Hope this helps

---

### Post by bOgNeR17 on 2012-05-13
Sorted, thank you glad I got it back to the way I wanted. Like to have my system free from software that will make it more sluggish.

---

### Post by JC Cheloven on 2012-05-13
> **bOgNeR17 said:**
> Sorted, thank you glad I got it back to the way I wanted. Like to have my system free from software that will make it more sluggish.
Yes, for sure ;)

If you have a moment, please mark as solved (see the red "thread tools" link at the top of the thread), so that others can do more efficient search.

Best
JC

---

