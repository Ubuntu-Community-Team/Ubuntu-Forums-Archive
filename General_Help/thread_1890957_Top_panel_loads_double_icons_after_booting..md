---
title: "Top panel loads double icons after booting."
date: 2011-12-04
forum: General Help
---

### Post by oxf on 2011-12-04
This is a reocurance of a little problem I've had before with erratic behaviour of applet icons in the upper panel of the desktop. I've never resolved it  but since the problem is usually gone after a reboot and only occurs sporadically gave up worrying about it.

But now after running some updates it there permanently..do HELP please!

Specifically the problem is this:

The battery and speaker icons are displayed twice. The lefthand pair are complete and fully functioning while the righthand pair are partially hidden by the left ones (and not functional) See the screenshot I've attached.

The only thing I can do is right click on the Left pair and delete them and then reinstall them from the "Add to Panel" menu. i.e the "Indicator Applet" This resolves the problem temporarilly but as soon as I reboot it's back to the double icons again.

As I said it's every time now. How do I fix this?

Thanks
Katja

---

### Post by westie457 on 2011-12-04
Hi this might not be a permanent fix however it does work without the need to reboot or log out the in again.

In a terminal run this ```
gconftool --recursive-unset /apps/panel && killall gnome-panel

```

---

### Post by oxf on 2011-12-04
> **westie457 said:**
> Hi this might not be a permanent fix however it does work without the need to reboot or log out the in again.

In a terminal run this ```
gconftool --recursive-unset /apps/panel && killall gnome-panel

```


Thanks!

Well after playing with the panel add/delete etc and many many reboots the problem seems to have resolved itself...for now that is. I'm sure it's only a matter of time before it will reapear. If it's just occasionally I guess I can (have to ) live with it. Obviously there's something unstable here that maybe there's no answer to?

Katja

---

