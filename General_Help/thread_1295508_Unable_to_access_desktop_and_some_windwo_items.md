---
title: "Unable to access desktop and some windwo items"
date: 2009-10-19
forum: General Help
---

### Post by rmcellig on 2009-10-19
For some reason I am unable to right mouse click on the desktop. Also, I cannot see the three buttons that appear in every window that allow me to close, minimize and expand a window. How to I get that functionality back?

I am using 9.0.4

Thanks!!

---

### Post by ram2500 on 2009-10-19
Have you tried restarting X? Since there is a program (dontzap) that prevents action from pressing Ctrl+Alt+Backspace (which restarts X), log out by pressing Ctrl+Alt+Delete instead of Backspace. It's probably a one-time issue.

---

### Post by rmcellig on 2009-10-19
I tried restarting my computer with the same results. Windows open up full screen, I am unable to resize any windows or right mouse click on the desktop, and I still can't see the three icons that appear on every window to close, minize and enlarge. Could this be a setting in Nautilus? How can I set it back to the default or is there something I can change in the Nautilus GUI settings?

---

### Post by P4man on 2009-10-19
are you using the netbook remix?

---

### Post by rmcellig on 2009-10-19
Yes I was trying it out. What is the best way for me to uninstall it? Could that be the cause?

---

### Post by P4man on 2009-10-19
yes its the cause. there was a bug in the switcher app that lets you switch between the netbook ui and the regular one. its possible to recover I think, but I dont know how. Perhaps someone else will fill in?

---

### Post by rmcellig on 2009-10-20
So does anyone have an answer to my problem :). Do I have do delete something or just change some settings? Very frustrating.  Can I safely dete the Switcher app? If so how do I do it?

Thanks for your help!!

---

### Post by P4man on 2009-10-20
Here is the bug report:
[https://bugs.launchpad.net/desktop-switcher/+bug/349519](https://bugs.launchpad.net/desktop-switcher/+bug/349519)

solutions are in there, feel free to post again if you're stuck trying any of them.

---

### Post by rmcellig on 2009-10-20
Hi P4man,

Thanks for the link to the thread but now I am really confused going through the thread. I just need some help (step by step) to exactly what I have to do to resolve my problem.

Thanks!!!

---

### Post by P4man on 2009-10-20
I dont know heh. Can you open a terminal ? Or alt+F2 ? Then try this:

```
gconftool-2 --set /desktop/gnome/session/required_components_list --list-type=string ["filemanager","panel","windowmanager"]
```

and reboot.

---

### Post by P4man on 2009-10-20
another thing to try is 

```
metacity --replace
```

---

