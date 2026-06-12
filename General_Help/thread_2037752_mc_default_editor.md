---
title: "mc default editor"
date: 2012-08-05
forum: General Help
---

### Post by icegood on 2012-08-05
> 
sudo update-alternatives --config editor 

returns 
```

 Selection    Path                Priority   Status
------------------------------------------------------------
  0            /bin/nano            40        auto mode
  1            /bin/ed             -100       manual mode
  2            /bin/nano            40        manual mode
  3            /usr/bin/emacs23     0         manual mode
  4            /usr/bin/mcedit      25        manual mode
  5            /usr/bin/vim.basic   30        manual mode
* 6            /usr/bin/vim.tiny    10        manual mode

```

but mc still opens files via GNU nano. WTF?

---

