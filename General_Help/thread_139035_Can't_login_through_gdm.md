---
title: "Can't login through gdm"
date: 2006-03-03
forum: General Help
---

### Post by Mlehliw on 2006-03-03
For some reason gdm won't let me login. When I enter my username/password it immediately goes back to the username prompt. No errors pop up at all. I know it's correct because if I enter in a wrong user/pass combo it does its usual 3 second pause.

I can still login through the console using ctrl+alt+#. Everything seemed still intact though I don't know where to begin looking for this type of problem. I've never changed any properties of gdm on this install so I'm kind of at a loss on where to start. Any ideas?

---

### Post by Mlehliw on 2006-03-03
Never mind, I figured it out. I had a command in gdm/PostLogin/Default script that pointed to a file I deleted, oops.

---

