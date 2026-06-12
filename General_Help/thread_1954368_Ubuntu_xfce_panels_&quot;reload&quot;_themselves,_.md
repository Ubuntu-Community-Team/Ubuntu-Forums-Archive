---
title: "Ubuntu xfce panels &quot;reload&quot; themselves, sometimes black screen as a result"
date: 2012-04-07
forum: General Help
---

### Post by sirriffsalot on 2012-04-07
Hello!

Quite recently my Ubuntu partition has gotten into some severe trouble it seems, and I really hope help can be provided quickly... 

At seemingly random times, my system freezes in such a way that, when I try to right-click on my desktop, the background relapses for a moment into the standard purple colour, and then goes back to my wallpaper, and this is the same behaviour of the "logout/shutdown" button (in the xfce-panel) and my other panel buttons such as Opera, VLC, et cetera.. Eventually, or at times, a black screen enters the scene and is accumulating an escalating skill in ticking me off, haha..

I really cannot spend another week on such problems as I have in the past, I would be most beholden to anyone who offer much assistance in this!

Cheers!

---

### Post by Peripheral Visionary on 2012-04-08
Xfce panels in Ubuntu? Perhaps you're using _X_ubuntu rather than _U_buntu? The combination of bits from the Xfce environment with the Unity environment is probably creating some conflicts. I love the Xfce panel, but it won't work in Unity I'm pretty sure. Try 

```
apt-get install xubuntu-desktop
```

and select Xfce or Xubuntu from the Session manager at boot-up if you want that sweet Xfce panel in it's native environment. And choose Ubuntu from the Session manager at bootup if you want that wonderful Unity dock! But they won't work in combination, I don't think.

---

### Post by sirriffsalot on 2012-04-08
Perhaps I should have mentioned that I am using Ubuntu Studios... :-/

---

