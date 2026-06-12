---
title: "Cannot set $TERM in GNU Screen"
date: 2009-12-14
forum: General Help
---

### Post by dnquark on 2009-12-14
On a fresh Karmic install, GNU screen ignores any attempt to set the TERM variable -- either by setting term="xterm-256color" in .screenrc, or using :term command in screen itself, or using a -T command line switch.  Whatever I do, $TERM is stuck at xterm.  Somehow screen is able to display 256 colors under gnome-terminal, but under xterm it defaults to 8, which makes sense since tput colors for xterm returns 8.  This seems to be a bug, is there a workaround?

---

