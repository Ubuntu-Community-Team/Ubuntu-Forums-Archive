---
title: "Devilspie set workspace"
date: 2011-08-16
forum: General Help
---

### Post by Triblaze on 2011-08-16
I have a terminal set up with devilspie to open when the computer starts. This terminal is set up to be like part of the desktop background, that is, decorations removed, set below other windows, etc.

All that works, but I want it to open in my sixth workspace (I have six workspaces, 3x2). For some reason, it always opens in the first workspace, the one that the computer loads on.

Devilspie file:
```
(if
        (matches (window_name) "DesktopConsole")
        (begin
                (set_workspace 6)
                (set_viewport 6)
                (below)
                (undecorate)
                (skip_pager)
                (skip_tasklist)
                (wintype "utility")
                (geometry "1110x660")
        )
)
```All the other stuff works, but setting the workspace doesn't. I'm not sure how setting the viewport factors in.

---

### Post by Habitual on 2011-08-16
```
killall -9 devilspie 
```
then run
```
gnome-terminal
```
then
```
devilspie -a
```

what does dp indicate?

---

### Post by Triblaze on 2011-08-25
Sorry for the late reply, was on vacation with no internet, that returns:

```
** (devilspie:7229): WARNING **: Workspace number 6 does not exist

(devilspie:7229): Wnck-CRITICAL **: wnck_window_move_to_workspace: assertion `WNCK_IS_WORKSPACE (space)' failed

```

Odd.

---

