---
title: "Can't change Gnome Commander prefered terminal"
date: 2009-10-01
forum: General Help
---

### Post by ToshibaLaptoplinux on 2009-10-01
I just installed Gnome Commander and like what I see so far.

But I would prefer it to use my Terminator program vs the Gnome Terminal but am not sure how to change it.

I added it to the Settings:options:programs:standard programs:terminal menu but when I click on the terminal icon it still launches Gnome terminal. Am I doing something wrong?

Thanks.

---

### Post by ToshibaLaptoplinux on 2009-10-02
Well I won't pretend to understand how or why but apparently Commander picks up the preferences from the preferred applications settings in Gnome and not the setting dialogue in its own preferences. I changed my preferred terminal to terminator in Gnome and now commander launches it instead of the xterm

Thanks anyway.

---

### Post by micklock on 2009-10-24
You are absolutely right. It uses gnome preferred application settings.
I fixed it with running
```
gnome-control-center
```
from within a terminal in my XFCE, went to Preferred Applications->System(tab), change terminal to Custom, type in
```
xfce4-terminal
```  (or whatever your preferred console is) and leave the ```
-x
``` option in there. Without it my terminal won't open from within Gnome Commander.
And you are all set. Both the button and context "Open Terminal Here" will use your favorite terminal.:P

Hope it helps.

---

