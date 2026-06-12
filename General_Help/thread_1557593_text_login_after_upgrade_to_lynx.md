---
title: "text login after upgrade to lynx"
date: 2010-08-21
forum: General Help
---

### Post by deviator on 2010-08-21
i just upgraded one of my computers to lucid lynx and when i rebooted i'm faced with a text log in.

after i login i just have a basic terminal prompt: no gui whatsoever.

during the upgrade process i received an error message along the lines of "could not install lib(iforgettherest).
i click cancel and it said it would revert my system to its original state. after it worked for a few minutes i checked the version and it was lynx.

rebooted and now no gui. any thoughts?:confused:

---

### Post by amac777 on 2010-08-21
Login, and then try this command to start the GUI login screen:

```
sudo service gdm start
```

You can also try running this command to load your desktop:

```
startx
```

If those work, you may just need to get the thre first command to auto run when you boot up.

---

### Post by deviator on 2010-08-21
startx did the trick thanks.

it's not perfect but i managed to log in.

sudo service gdm start was already running.:D

---

