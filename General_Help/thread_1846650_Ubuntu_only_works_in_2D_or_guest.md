---
title: "Ubuntu only works in 2D or guest"
date: 2011-09-19
forum: General Help
---

### Post by hardisty on 2011-09-19
So I just posted this in my thread about my dwindling filesystem root space, but I think that's an unrelated issue, so I'm making this new thread. Sorry if that's bad form, I'm new to Linux and haven't used a message board in years.

I'm stuck using only Ubuntu 2D for my main account. Signing in as a guest works fine, but Non-2D version of my admin account gives me no taskbar options like mail, wifi, power options, etc. Only the options of "File, Edit, View, Go, Bookmarks, Help"

---

### Post by hardisty on 2011-09-19
tried "unity --reset" with no luck, but it did say "unity-panel-service no process found"

---

### Post by stueytheboy on 2011-10-23
I'm having the same issue.

---

### Post by okdimok on 2011-11-05
For me the same problem was caused by turned of Unity plugin in Compiz Config. I'm sure I haven't done that myself, so I don't know the exact reason, but I have a solution:

[LIST]
[*]You login to your Ubuntu, where nothing works. (Not Ubuntu 2D, the Ubunut you usually loading)
[*]You run the terminal emulator by pressing Ctrl+Alt+T.
[*]You run ccsm command in it. It starts CompizConfig Settings Manager.
[*]There you enable unity plugin.
[*]Reboot or relogin is needed to finish recovery.
[/LIST]

---

