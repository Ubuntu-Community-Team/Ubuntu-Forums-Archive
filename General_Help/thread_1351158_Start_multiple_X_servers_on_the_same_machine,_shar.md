---
title: "Start multiple X servers on the same machine, sharing mouse and keyboard"
date: 2009-12-10
forum: General Help
---

### Post by Pierre-Étienne Messier on 2009-12-10
Hello,

I currently have a machine that have 2 monitors. X is configured as dual screen. I have 1 mouse/keyboard for the 2 screens.

Because of one specific program, the X server currently doesn't run the XRender (RENDER) extension (both are incompatible). But we have to enable it for at least one screen. Since we can't just enable the extension for 1 screen only, the current option we're looking at is to start 2 different X servers with 2 different configs (one with XRender, one without) on the 2 different screeens.

Would it be possible to run 2 X servers at the same time, on 2 different monitors, and share 1 mouse and 1 keyboard between the 2 displays?

Thank you!

---

