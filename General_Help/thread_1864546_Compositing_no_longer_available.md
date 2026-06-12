---
title: "Compositing no longer available"
date: 2011-10-19
forum: General Help
---

### Post by ofnuts on 2011-10-19
My window compositing suddenly no longer works:
- no "glow" around the active window
- no window transparency
- 5px black frame around windows popped out by the widget bar

When I open the desktop settings (Desktop effects), it says "Compositing temporarily disabled". I can click the resume button, it says "Compositing is active" but nothing changes on the desktop, I w old even says that this is plain ignored (compositing changes due to battery status are quite visible since every windows is redrawn).

I have power profiles that disable compositing, but they aren't in use, and I check that the current ones don't.

I have a Core I5 with integrated graphics, so it's not the graphic cards that moved in the connector. lspci says: ```
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
```

I did logoff/login, then reboot, then power off/power on.

Since I had a recent kernel upgrade, I booted on the previous kernel.

Anything else to check/try?

---

