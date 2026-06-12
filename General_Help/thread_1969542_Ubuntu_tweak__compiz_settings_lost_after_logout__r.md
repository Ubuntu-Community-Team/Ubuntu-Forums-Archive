---
title: "Ubuntu tweak / compiz settings lost after logout / reboot"
date: 2012-04-30
forum: General Help
---

### Post by tristan on 2012-04-30
Hi all. All of the improvements have me back on ubuntu after 12 months unsatisfied distro hopping. Really loving 12.04 so far. I've used ubuntu tweak 0.7 to fine tune the experience. It works really well except for one minor irritation:

I use tweaks/workspace to set up compiz "show windows" using the top left screen corner, and "show workspaces" using bottom left. All works really well, until I log out or reboot. Upon logging back in, the active corners no longer work. I can start ubuntu tweak and tweaks/workplaces shows the corners to be assigned, however I have to unassign and reassign them to get them to work again.

I wonder if anyone else has seen this (I've seen it on the 3 computers I've installed 12.04 on), or knows of a fix. Or if anyone knows the correct gconf keys to edit to set up this behaviour manually. 

TIA

---

### Post by etoet on 2012-05-02
> **tristan said:**
> Hi all. All of the improvements have me back on ubuntu after 12 months unsatisfied distro hopping. Really loving 12.04 so far. I've used ubuntu tweak 0.7 to fine tune the experience. It works really well except for one minor irritation:

I use tweaks/workspace to set up compiz "show windows" using the top left screen corner, and "show workspaces" using bottom left. All works really well, until I log out or reboot. Upon logging back in, the active corners no longer work. I can start ubuntu tweak and tweaks/workplaces shows the corners to be assigned, however I have to unassign and reassign them to get them to work again.

I wonder if anyone else has seen this (I've seen it on the 3 computers I've installed 12.04 on), or knows of a fix. Or if anyone knows the correct gconf keys to edit to set up this behaviour manually. 

TIA


exactly same issue here &#12290;&#12290;&#12290;

---

### Post by etoet on 2012-05-02
> **tristan said:**
> Hi all. All of the improvements have me back on ubuntu after 12 months unsatisfied distro hopping. Really loving 12.04 so far. I've used ubuntu tweak 0.7 to fine tune the experience. It works really well except for one minor irritation:

I use tweaks/workspace to set up compiz "show windows" using the top left screen corner, and "show workspaces" using bottom left. All works really well, until I log out or reboot. Upon logging back in, the active corners no longer work. I can start ubuntu tweak and tweaks/workplaces shows the corners to be assigned, however I have to unassign and reassign them to get them to work again.

I wonder if anyone else has seen this (I've seen it on the 3 computers I've installed 12.04 on), or knows of a fix. Or if anyone knows the correct gconf keys to edit to set up this behaviour manually. 

TIA

fixed. 

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/858845](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/858845)

You can work around the bug by setting expo plugin to be loaded after unityshell:
Just edit /apps/compiz-1/general/screen0/options/active_plugins key in gconf-editor and place expo under unityshell


simillary, place scale under unityshell. 

:)

---

### Post by tristan on 2012-05-02
Phew, good to see I wasn't the only one. I just created a little bash script to clear and rewrite the gconf entries thusly:

```
gconftool-2 --unset "/apps/compiz-1/plugins/scale/screen0/options/initiate_all_edge"

gconftool-2 --unset "/apps/compiz-1/plugins/expo/screen0/options/expo_edge"

gconftool-2 --set "/apps/compiz-1/plugins/scale/screen0/options/initiate_all_edge" --type string "TopLeft"

gconftool-2 --set "/apps/compiz-1/plugins/expo/screen0/options/expo_edge" --type string "BottomLeft"

notify-send "Compiz fx enabled"
```

I set up a keyboard shortcut for it and all is good. Happy to know it will be fixed though.

---

### Post by iain_m2 on 2012-05-10
that script is great thanks. Works fine. I have looked into how to change the expo function for show desktop but have run into the buffers and cannot get it to do what I want which is to show the desktop when I place the mouse cursor in that corner. Any ideas?

---

### Post by kokonobs on 2012-05-13
Amazing how u will never be the only one facing as issue. Same issue here. I just posted a question to Ask Ubuntu regarding this.

---

### Post by krakonos on 2013-02-18
Is it fixed now? - looks like persistent problem - but its not suprisse

---

### Post by Tryfon on 2013-03-15
I have been facing the same problem for a long time. Recently I thought of trying to use CompizConfig Settings Manager to configure the edge settings for the window picker and show desktop instead of Ubuntu Tweak. Now settings are kept even after I reboot. Problem solved finally.
I am not sure if it is an Ubuntu Tweak specific problem, or if CompizConfig Settings Manager developers found a way to tackle the issue. What matters for me is that it is seems solved now and forever, but it would be better if other users confirmed the behaviour as well.

---

