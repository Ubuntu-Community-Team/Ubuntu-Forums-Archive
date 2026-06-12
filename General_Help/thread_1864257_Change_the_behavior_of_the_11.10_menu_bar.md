---
title: "Change the behavior of the 11.10 menu bar?"
date: 2011-10-18
forum: General Help
---

### Post by IQAndreas on 2011-10-18
The way the "menu bar" for individual applications works in 11.04 and 11.10 seems very counter-intuitive to me (perhaps because I have never been a MAC user.

I want the menu bar to behave in a manner summed up in this image:
[[IMG]http://iqandreas.isbetterthanyou.org/public/ubuntuforums.org/ubuntu-menubar-behavior-suggestion-scale50.png[/IMG]]("http://iqandreas.isbetterthanyou.org/public/ubuntuforums.org/ubuntu-menubar-behavior-suggestion.png")
[LIST]
[*]The top "menu bar" belongs to the topmost fullscreen application (in the example, Chrome) if there is one available.
[*]If a running application is not fullscreen (in the example, GEdit), it will have its own menu bar which becomes visible when you hover over its "window bar".
[*]Clicking the top menu bar will bring you to the topmost fullscreen application (in the example, Chrome) just as if you had clicked anywhere inside the application's fullscreen window.
[/LIST]

Are there any settings that can be tweaked or any extensions that allow such behavior?

Also, what is the name of the program I want to modify the behavior of? Gnome? XOrg? Compiz? I don't quite understand where the line between those software packages is.

---

### Post by JaredSi on 2011-10-18
I also would like to know this, I made a post earlier about this but received no reply's.

Edit: I actually just stumbled across this which did what I wanted it to do, [http://askubuntu.com/questions/10481/does-unity-support-disabling-the-global-application-menu](http://askubuntu.com/questions/10481/does-unity-support-disabling-the-global-application-menu). Just run this > sudo apt-get remove indicator-appmenu then log out and log back in, hope this helps.

---

### Post by IQAndreas on 2011-11-03
Thank you JaredSi! Uninstalling "indicator-appmenu" worked like a charm.

I just wish clicking the "top bar" would still bring you to the current fullscreen application, but oh well, it's good enough as it is.

---

