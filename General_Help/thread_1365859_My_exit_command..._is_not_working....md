---
title: "My exit command... is not working..."
date: 2009-12-27
forum: General Help
---

### Post by squareff255 on 2009-12-27
When I'm in a terminal and I type "exit" it simply prints "exit" on the next line and the cursor then jumps to the 3rd line like it's processing something... Is there anyway to fix that like editing some file in /bin/?????? or... something?

---

### Post by Marvin666 on 2009-12-27
Which terminal are you using, the ctrl alt one, or the one from the applications menu?

---

### Post by 3rdalbum on 2009-12-27
Actually now that you mention it, I sometimes get this when I 'ssh' into my home server. It prints 'logout' and then just pauses for eternity. This doesn't always happen, but it seems to happen more when I've been connected for a while.

I'm using Gnome Terminal.

---

### Post by falconindy on 2009-12-27
> **3rdalbum said:**
> Actually now that you mention it, I sometimes get this when I 'ssh' into my home server. It prints 'logout' and then just pauses for eternity. This doesn't always happen, but it seems to happen more when I've been connected for a while.

I'm using Gnome Terminal.
I notice this behavior occasionally when I forward X extensions. The connection closes properly, but for some reason the session itself never terminates. I believe you can just use C-c to get out of it.

---

