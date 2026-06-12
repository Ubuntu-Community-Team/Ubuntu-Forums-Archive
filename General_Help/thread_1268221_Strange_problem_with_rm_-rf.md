---
title: "Strange problem with rm -rf"
date: 2009-09-16
forum: General Help
---

### Post by PixelSmack on 2009-09-16
Ok this is a sort of solved problem, however i am still interested in the theory behind it..

I have been building chromium from source for a while now, and decided to get rid of the src directroy and all of my current builds and start from scratch (change of build config). So i wanted to use rm -rf to delete the ./src/ dir. the ./src/out/Debug/ dir was symlinked to /opt/chrome and the binary was linked on my gnome-Do docky bar.

When trying to rm -rf the src directory, after a second or so i got a total lockup of my gui, nothing responded including attempts to change runlevels. The box still responded to a ping although not having openssh-server installed didn't allow me to try anything else, so i hard rebooted. This happened twice. The third time i removed both the symlink dir and the gnome-Do icon and the delete worked... Does anybody have any clue what happened here and what may have caused it..

---

