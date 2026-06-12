---
title: "Making A Keyboard Shortcut That Can Kill Fullscreen Applications?"
date: 2012-03-03
forum: General Help
---

### Post by jlacroix on 2012-03-03
Hello all, I have a very strange problem.

I'm trying to write a script that will force close several applications. I saved the script in /usr/local/bin and set up a keyboard shortcut to it in XFCE. The script works, but only if the application is not fullscreen:

```

#!/bin/bash
# init

killall vlc
killall zsnes
killall frozen-bubble


```
I don't understand why fullscreen would matter. Is there any way to set up a keyboard shortcut to run this script regardless of whether or not an application is running full screen?

---

