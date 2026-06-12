---
title: "Latest Octave in 10.04"
date: 2011-09-09
forum: General Help
---

### Post by NoBugs! on 2011-09-09
I'm trying to install the latest stable Octave (it seems there is no package ppa yet). when I run ./configure it ends with the error:
```

...
checking for struct group.gr_passwd... no
checking for tputs in -lncurses... yes
checking for rl_set_keyboard_input_timeout in -lreadline... no
configure: WARNING: I need GNU Readline 4.2 or later
configure: error: this is fatal unless you specify --disable-readline

```

Am I missing a library that needs to be installed? Should I disable readline??

---

### Post by TeoBigusGeekus on 2011-09-09
Try to install readline
```
sudo apt-get install readline
```

---

### Post by NoBugs! on 2011-09-09
E: Couldn't find package readline

---

### Post by TeoBigusGeekus on 2011-09-09
Hm...
Open Synaptic Package Manager and do a search for readline.

---

### Post by NoBugs! on 2011-09-09
Readline-common was installed, but libreadline6-dev wasn't, installing that seems to fix it :)

---

### Post by TeoBigusGeekus on 2011-09-09
Good to know...
I'm glad you got it fixed!

---

