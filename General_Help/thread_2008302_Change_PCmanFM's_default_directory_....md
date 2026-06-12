---
title: "Change PCmanFM's default directory ..."
date: 2012-06-22
forum: General Help
---

### Post by Bucky Ball on 2012-06-22
Hi all,

As per the title: When I launch PcmanFM I'd like to select the directory it opens to rather than have it open to /home.

I've hunted around but found no clues ...

Any thoughts?

---

### Post by kanikilu on 2012-06-22
I'm not sure that is configurable. It's been a while since I've used XFCE for any length of time, but I'm sure you can edit launchers. Just change the launcher of pcmanfm to point to the directory of your choosing.

For example, "pcmanfm ~/Desktop" would point it to your desktop instead of your home directory.

The XFCE getting started guide says: > You can right-click on any panel item to get a menu that allows you to change its properties...

That takes care of the GUI. To do the same for CLI, just add an alias to ~/.bashrc (or ~/.bash_aliases). Add:

```
alias pcmanfm='pcmanfm ~/Desktop'
```

---

### Post by Bucky Ball on 2012-06-22
> **kanikilu said:**
> 

For example, "pcmanfm ~/Desktop" would point it to your desktop instead of your home directory.



Thanks, you're a legend. That worked perfectly! Such a simple and elegant solution.

I don't use icons for anything, all keyboard hotkeys, so I just opened Keyboard Shortcuts and added this as the command:

pcmanfm ~/mydirectory

... and <super>+j for a testing hotkey and no problems.

Solved. ;)

---

