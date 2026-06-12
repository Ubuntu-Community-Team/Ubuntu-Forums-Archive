---
title: "Unity has disappeared."
date: 2011-11-15
forum: General Help
---

### Post by blackplague1347 on 2011-11-15
I apologize if this has been addressed elsewhere; I can't find it.

Couple days ago, my DE froze. I switched to another console (ctrl-alt-F6) to make sure it wasn't the entire system. Since it wasn't, I decided to restart my DE. It has worked before, so I assumed it would this time as well. 

I ran:
```
sudo /etc/init.d/lightdm restart
```

Well, it worked, sort of. I wasn't frozen anymore, but apparently Unity isn't happy with me, because it's been in hiding ever since. No launcher. Nothing pops up when I hit the Windows key on my keyboard. I start pretty much everything from the terminal.

I attached a screencap of my default desktop.

Also, Unity 2D works as normal, which is good, but I'd rather not have to use 2D when I'm fully capable of using "normal" Unity.

---

### Post by elliotn on 2011-11-15
did u try to start unity via terminal?
I had the same problem but I had Cairo dock with terminal launcher so I just stated unity via teminal

---

### Post by Mark Phelps on 2011-11-15
I had something similar happen to me -- because I made the mistake of opening Compiz Configs Settings Manager (ccsm).

The solution that worked for me is detailed in the link below:

[http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html]("http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html")

---

