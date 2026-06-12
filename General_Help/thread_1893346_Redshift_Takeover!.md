---
title: "Redshift Takeover!"
date: 2011-12-10
forum: General Help
---

### Post by mxndrwgrdnr on 2011-12-10
Installed redshift to adjust the color of my monitor. Now I cannot toggle redshift on/off, and when I quit redshift altogether, nothing happens. Furthermore, I notice that the installation of the redshift indicator seems to have killed my weather indicator? Any ideas???

---

### Post by mcduck on 2011-12-10
What did you expect to happen when you stop it from running? Nothing is supposed to happen... (if you were running at some other than normal color temperature when you quit redshift, that color temperature would be left active. Redshift doesn't constantly change the color or isn't even the one handling the color change, it simply forwards a command to another program that's responsible of your display. So you may want to shift back to normal color before you quit or uninstall redshift.

...and how did it "kill" your weather indicator icon? If you are talking about not being able to click some of the indicators to open their menus when redshift icon is visible in the indicator area, that's a known bug of the indicator applet itself; configuring it to allow "all" icons causes problems with using mouse to click the menus, clicking a working icons and then using keyboard to navigate works fine. The solution for that is to whitelist the exact programs you want instead of allowing "all" icons.

---

