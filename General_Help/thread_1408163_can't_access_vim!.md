---
title: "can't access vim!"
date: 2010-02-16
forum: General Help
---

### Post by engine on 2010-02-16
According to synaptic, vim-common and vim-tiny are installed; according to which vim, which vim-tiny and which vim-common, they aren't :-{ So how can I track down my vim installation and add a start-up link to my UNR favourites?

---

### Post by Satoru-san on 2010-02-16
Can you post the results of this?

```
sudo updatedb
locate vim
```

you maybe want to try which vi :)

---

### Post by engine on 2010-02-16
Just the tip I needed - thanks! Turns out that while the app is called tiny-vim, the command is tiny.vim ...

---

