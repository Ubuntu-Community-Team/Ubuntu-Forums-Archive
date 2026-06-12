---
title: "Minimizing WINE apps makes them disappear"
date: 2010-10-22
forum: General Help
---

### Post by Kjella on 2010-10-22
Hello,

After installing Maverick 64 bit (clean install, used to be 32 bit Lucid) any applications I run in WINE disappear when I minimize them. They don't crash, they're just impossible to reach as they're no longer in task manager, they don't show up through alt-tab but I can see them if I run ps -x from a terminal. I tried with mIRC and the client is still responding, it'll still accept files with auto-get on so it's working fine, but the UI is gone.

Any suggestions?

---

### Post by ankspo71 on 2010-10-24
> **Kjella said:**
> Hello,

After installing Maverick 64 bit (clean install, used to be 32 bit Lucid) any applications I run in WINE disappear when I minimize them. They don't crash, they're just impossible to reach as they're no longer in task manager, they don't show up through alt-tab but I can see them if I run ps -x from a terminal. I tried with mIRC and the client is still responding, it'll still accept files with auto-get on so it's working fine, but the UI is gone.

Any suggestions?

Hi, which applications other than mIRC disappear from the taskbar when you use the minimize button. Is it all applications... even the notepad that comes with wine, or just the ones that are normally supposed to minimize to the system tray? Maybe they aren't appearing in the system tray is what I mean. I am thinking that *maybe* this is what it could be if mIRC was still running and responding. Try configuring mIRC to always show in the taskbar, or tell it not to use the system tray, if at all possible.

---

