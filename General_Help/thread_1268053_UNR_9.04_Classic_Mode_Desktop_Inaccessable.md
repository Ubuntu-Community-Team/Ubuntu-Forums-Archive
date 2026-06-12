---
title: "UNR 9.04 Classic Mode Desktop Inaccessable"
date: 2009-09-16
forum: General Help
---

### Post by mjohns930 on 2009-09-16
I am currently running UNR 9.04 on my EeePC 1005HA. I am using it in the classic mode without the launcher. I am having an issue where I can't do anything with the desktop. When I download something to it, it does not show up there it just shows up in ~/Desktop. If I right click on it, it gives me no menu, if I try to drag and drop something on it, it won't let me.

I am assuming it has something to do with the fact that I installed UNR, but for the life of me I cannot figure it out. I am still fairly new to this so I don't really know where to look.

Any help is appreciated.

Thanks

---

### Post by Brandon Williams on 2009-09-16
How did you switch to classic mode? Did you just reconfigure manually? If so, you might not be running nautilus in desktop manager mode.

Try running this command, and then logout and back in.
```
gconftool-2 --set /desktop/gnome/session/required_components_list --list-type=string ["filemanager","panel","windowmanager"]
```

---

### Post by mjohns930 on 2009-09-17
I switched back by using the switch desktop mode option in System>Preferences. 

I tried running your command and it gives me this:

```
$ gconftool-2 --set /desktop/gnome/session/required_components_list --list-type=string ["filemanager","panel","windowmanager"]
Must specify a type when setting a value
```

---

### Post by Brandon Williams on 2009-09-17
I should have scrolled down a bit further in [this bug report](https://bugs.launchpad.net/desktop-switcher/+bug/349519), where you can get more information. This is a problem called out in the release notes. Always a good idea to read them before an install.

This should work. If not, read the bug report to get more ideas.
```
gconftool-2 --set /desktop/gnome/session/required_components_list --type list --list-type=string ["windowmanager","panel","filemanager"]
```

---

### Post by mjohns930 on 2009-09-17
Success! All is working how it should now.

Thanks for finding that for me. I didn't even think to look through the bug reports and all the searching I did brought me no where even close to that.

---

