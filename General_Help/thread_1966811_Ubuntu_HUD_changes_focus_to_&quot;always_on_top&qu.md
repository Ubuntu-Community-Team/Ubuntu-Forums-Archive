---
title: "Ubuntu HUD changes focus to &quot;always on top&quot; window."
date: 2012-04-27
forum: General Help
---

### Post by balthamaisteri on 2012-04-27
Hi,

I have proble with ubuntu 12.04, HUD (behind alt-key) changes focus from selected window to any window which happends to have "always on top" selected (most likely vlc-player).

Focus changes when HUD is shutting down. Sometimes this happends if system is doing something like installing updates.

This was driving me almost crazy, so I had to turn HUD off with ubuntu tweak.

Running Ubuntu 12.04 64bit.

Any help with this one? :P

Thanks.

---

### Post by PLP84 on 2012-05-03
I have the same problem and it is very annoying (also Ubuntu 12.04 64bit).
However it is not the HUD. The same thing happens if you open a preferences window for example (in Firefox I open Edit->Preferences, then hit Esc the focus goes to the "Always on top" window)

I tried to change the settings in Compiz (auto raise and focus) but it didn't help.
On Unity 2D this does not happen.

If anyone has any idea....

Thank you...

---

### Post by albertoueda on 2012-11-06
Hi, I had the same problem and I solved finding the problematic extension/plugin.

In my case, the extension that was the "Global Menu Bar integration 3.5.4", which integrates the FF menu to the Unity panel. When I disabled it and restarted the FF, the "always on top" problem was solved.

[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1023683](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1023683)

---

