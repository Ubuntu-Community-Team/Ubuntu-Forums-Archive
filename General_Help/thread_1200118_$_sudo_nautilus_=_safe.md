---
title: "$ sudo nautilus = safe?"
date: 2009-06-29
forum: General Help
---

### Post by viking_maniac on 2009-06-29
The first thing that really irritated me about Ubuntu Linux was the restriction in the Nautilus file-system explorer for root permissions. But *whola* by writing **$ sudo nautilus** in the terminal, I was suddenly in the Nautilus as root and could do anything and everything. But is it safe to even run that command like that? I get some warnings or error messages by doing it--try it yourself and see--if you dare.

---

### Post by SuperSonic4 on 2009-06-29
You should use ```
gksu nautilus
``` for launching a graphical app.

It's perfectly safe to run that command - it's what you do after it that could cause a problem. A lot of users need to edit system/config files and to do that root priveliges are needed

---

### Post by Monotoko on 2009-06-29
It is a safe and practised way of editing files, however you would be best using gksudo rather than sudo

However, user mistakes make it not safe, it is not advised for use unless you REALLY need to edit something which your user cannot do, and when you have done it you are advised to close it again.

What you can do as your own user, do as your user, dont run anything as root unless you really need it!

---

### Post by CatKiller on 2009-06-29
As others have already pointed out, [gksudo]("http://www.psychocats.net/ubuntu/graphicalsudo") is the appropriate tool for graphical applications with elevated privileges.

One tip that I picked up here some time ago is to make root's nautilus window as unpleasant as you can to discourage abuse. I went for a salmon-pink background for mine so that red would inspire caution, but it was still easy to see stuff. It's exceptional that you should ever need to use nautilus as root; open it for one specific task and close it again as soon as you've finished what you needed to do. Using it day-to-day is begging for breakage.

---

