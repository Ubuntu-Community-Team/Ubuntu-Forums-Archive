---
title: "Alt + Tab problem"
date: 2009-11-02
forum: General Help
---

### Post by 7raTEYdCql on 2009-11-02
On my earlier ubuntu, alt+tab would shift to the next window, on the same workspace. 

alt+shift+tab would shift to the previous window. on my newly installed alt+shif+tab,doesn't work at all. What can the problem be?

---

### Post by Aero-Z on 2009-11-02
> **i.mehrzad said:**
> On my earlier ubuntu, alt+tab would shift to the next window, on the same workspace. 

alt+shift+tab would shift to the previous window. on my newly installed alt+shif+tab,doesn't work at all. What can the problem be?
I'm not sure but maybe you have to install CompizConfig Settings Manager. There's definately a setting for that shortcut.

---

### Post by 7raTEYdCql on 2009-11-03
That is weird. It would work by default on my earlier ubuntu.

---

### Post by xoddam on 2009-11-08
Same issue here

The binding under gconf-editor -> apps -> compiz -> plugins -> switcher -> allscreens -> options -> prev_key is unchanged

so I don't think messing with settings is going to fix this.

I do believe the alt-shift combination is being grabbed or mapped by something else.

Workaround: The prev_all_key (ctrl+shift+tab) still does the same thing (though it's cross-workspace; I don't use multiple workspaces so it's effectively the same thing for me).

---

### Post by xoddam on 2009-11-09
Solved (for me, YMMV)

It turns out it's the same bug as some people saw last dist-upgrade (or two, even) though for some reason I didn't experience it myself before.

Maybe this is actually the first dist-upgrade I've done since the last full install (on an Ubuntu machine running compiz).

Metacity settings override compiz ones.  WHY?

gconf-editor -> apps -> metacity -> global_keybindings -> switch_windows_backward

was not set

changed it to <Alt><Shift>Tab and alt+shift+tab works again.

---

### Post by gcummins on 2009-11-10
Thanks, xoddam. That fixed it for me as well.

---

### Post by robinparriath on 2009-11-10
Thanks xoddam (or is it maddox?)

That fixed my issue too...  This is listed as a bug in launchpad. [Bug#326199]("https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/326199")

Posted your solution there.  Hopefully, we will get the fix in the next update.  :D

---

### Post by 7raTEYdCql on 2009-11-11
I got this by simply installing ccsm, and setting my preferences.

---

### Post by almalaci on 2009-11-12
Thanks xoddam, it did the trick for me too.

---

