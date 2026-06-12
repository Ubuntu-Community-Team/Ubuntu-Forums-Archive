---
title: "Tmux autostart with two panels?"
date: 2012-09-24
forum: General Help
---

### Post by casbahdk on 2012-09-24
I have added the following to my .bashrc to start when I open a terminal:```
[[ $TERM != "screen" ]] && exec tmux
```I would like to have tmux start with the equivalent of "C-b %" (in my case "C-a %" as I changed the keymapping in my tmux.conf). This should open two panes, right next to each other.

---

