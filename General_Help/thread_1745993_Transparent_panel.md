---
title: "Transparent panel"
date: 2011-05-01
forum: General Help
---

### Post by S. Vaden Blue on 2011-05-01
How do I go about enabling the transparent panel in Xubuntu 11.04? There doesn't seem to be a dialog for that in the panel settings and, if I'm correct, that is supposed to be an added feature in XFCE 4.8. Am I missing something?

---

### Post by keithpeter on 2011-05-01
> **S. Vaden Blue said:**
> How do I go about enabling the transparent panel in Xubuntu 11.04? There doesn't seem to be a dialog for that in the panel settings and, if I'm correct, that is supposed to be an added feature in XFCE 4.8. Am I missing something?

Hello S. Vaden Blue

Try right clicking over the panel in question, selecting Panel | Panel Preferences and then selecting the Appearance tab.

You should see a 'background' section in the top of the dialog. Try changing the 'Alpha' slider. If that does not change the panel try changing the Style setting. I can't remember what the default was and I've been customising! 

If the 'Alpha' setting has no effect, check if the 'compositor' is set on your system. I think it is by default, but that may depend on video drivers.

Menu | Settings | Settings Manager | Window Manager Tweaks | Compositor and see if 'enable display composting' is checked.

[http://bodmas.org/xubuntu-docs/config-desktop.html#customizing-panels](http://bodmas.org/xubuntu-docs/config-desktop.html#customizing-panels)

is what the help files say in Xubuntu

---

### Post by S. Vaden Blue on 2011-05-01
Thanks, keithpeter. Didn't think about the compositor as I don't use it often, or at all for that matter. Do now though.

Thanks again.
S. Vaden Blue

---

