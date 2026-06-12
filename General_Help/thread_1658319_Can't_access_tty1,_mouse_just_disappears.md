---
title: "Can't access tty1, mouse just disappears"
date: 2011-01-02
forum: General Help
---

### Post by Kareeser on 2011-01-02
Looks like I can't access tty1 for whatever reason. When I press ctrl-alt-F1 (to F6), my mouse just disappears.

Truth be told, I'm probably actually getting there, but I can't "see" it. All I see is what I had on my screen in tty7, but sans mouse.

Weird. Any ideas?

---

### Post by jeicrash on 2011-01-02
Usually tty1-6 are command line only and mouse usually will not show up unless you have enabled mouse in console. If your not getting a black screen with a prompt try pressing enter and see if the prompt is simply off the screen.

If you seeing your desktop it could be something with the video not switching properly. Or you may be running multiple X sessions. A little more info may be needed. What version / distro are you running? What Kernel, Have you modified any settings recently? That kind of info can help out a good deal.

Thanks.

---

