---
title: "can I use a Launcher to incr/decr VLC volume?"
date: 2010-11-08
forum: General Help
---

### Post by tobytoby on 2010-11-08
I am writing an application where I prefer having VLC being run in non-gui mode. To increase/decrease volume, the idea is to have a Launcher with appropriate code attached to it.
Is this possible? How should I do? Can I connect the Launcher to the hotkeys in some way perhaps? Or another solution?
Thanks for your input!

---

### Post by mc4man on 2010-11-08
Well  you could enable 'global hotkeys' for volume up and down, those will work with a dummy interface vlc (cvlc

you have to choose carefully w/ global hotkeys so there is no conflict or unintended result

As far as a 'launcher', if you mean like a desktop or panel launcher then you'd need 2, 1 up, 1 down, though a quick test here using xdotool suggests a panel launcher will work just fine,  a desktop one will not
(though you may be thinking something quite different

---

