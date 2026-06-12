---
title: "Openbox broken after upgrade"
date: 2006-06-02
forum: General Help
---

### Post by jworr on 2006-06-02
I like using the openbox window manager instead of metacity but after the upgrade to dapper it doesn't work properly anymore.  It still acts as a window manager (it draws boarders on windows and such) but open windows don't show up in the workspace switcher or the window list

my only configuration for openbox is this in ~/.gnome2/session file

I changed this:
0,RestartCommand=gnome-wm --sm-client-id default0

to this:
0,RestartCommand=gnome-wm --default-wm openbox --sm-client-id default0

it worked for 5.10 but now it doesn't any ideas?

---

