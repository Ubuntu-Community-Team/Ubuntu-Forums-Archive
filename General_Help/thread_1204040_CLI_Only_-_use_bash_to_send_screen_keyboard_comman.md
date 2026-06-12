---
title: "CLI Only - use bash to send screen keyboard commands?"
date: 2009-07-04
forum: General Help
---

### Post by Jose Catre-Vandis on 2009-07-04
I use my headless cli server to run many things, so use "screen" to open up various sessions get things running and then detach.

Is there any way to write a script in bash to simplify the access to a specific screen, to avoid the additional keyboard commands required by screen?

For example:

1. ssh into server
2. screen -r (to access last screen used)
3. CTRL+a +N (to move to next screen) or CTRL+a +1 (to move to screen 1)

It's the items in 3 that require physically entering.

I tried xmacros, but that needs x server running to work.

Any suggestions?

---

