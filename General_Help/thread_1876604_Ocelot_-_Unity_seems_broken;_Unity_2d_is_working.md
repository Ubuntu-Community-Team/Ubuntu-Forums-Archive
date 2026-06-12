---
title: "Ocelot - Unity seems broken; Unity 2d is working"
date: 2011-11-06
forum: General Help
---

### Post by lvshankar on 2011-11-06
I recently installed 11.10 on my Dell Vostro 1510. I was previously using Lynx and I didn't like Unity too much. So went ahead and did

```
sudo apt-get install gnome-panel
```

I thought I'd get the old Gnome look but it wasn't quite so - no System menu, couldn't add stuff to the panel etc

So I started playing around (even installed compizconfig-settings-manager and then removed compiz by mistake, then reinstalled it too. Basically, a lot of screw up ](*,))

I also reinstalled unity using apt-get. Now when I [auto-]login I am taken to Unity which looks like the attached file; theres is no launcher bar at all. But Unity 2D seems ok. However, I'd applied some key bindings in Compiz (mouse over the bottom left to show desktop) before I uninstalled compizconfig-settings-manager and it seems to still be active in Unity but not Unity 2D.

[LIST=1]
[*]How do I get Unity working properly?
[*]If not, how can I set Unity 2D to be default (there doesn't seem to be Login screen under System settings)
[*]How come the key bindings apply for Unity and not Unity 2d. Can I do something about it without reinstalling the manager?
[*]I also unchecked "volumes_visible" from the Configuration Editor under /apps/nautilus/desktop but a Ext2 volume still shows up on my Desktop (both Unity and Unity 2d). *Note*: Configuration Editor also said: "(!) This key has no schema" when I select that entry. Is that a bother?
[/LIST]


Thanks in advance!

---

### Post by lvshankar on 2011-11-08
bump! :confused:
Also, Ubuntu doesn't "remember" my preference of logging into Ubuntu 2D if I turn on automatic login

---

### Post by lvshankar on 2011-11-27
This fixed it:

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/875246](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/875246)
Closing

---

