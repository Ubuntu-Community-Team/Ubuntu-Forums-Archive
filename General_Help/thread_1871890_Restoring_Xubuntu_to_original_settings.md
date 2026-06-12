---
title: "Restoring Xubuntu to original settings"
date: 2011-10-29
forum: General Help
---

### Post by Ric_NYC on 2011-10-29
I want to start Xubuntu the way it was when I installed it.

How can I do that?

Thanks!

---

### Post by mike555 on 2011-10-29
If you don't remember how you changed it then backup your files and reinstall.

---

### Post by alco75 on 2011-10-29
If you want to remove other packages, see [here]("http://www.psychocats.net/ubuntu/purexfce"). That helped me to get rid of packages after upgrading Ubuntu Natty to Xubuntu Oneiric.

---

### Post by Toz on 2011-10-29
If you're talking about getting rid of all the customizations and configuration changes you made and reverting back to xubuntu factory settings, I would suggest the following:

1. Log out.
2. Ctrl+Alt+F1 to get to first vt
3. Log in to text session
4. Run the following commands:
```

mv ~/.cache/sessions ~/.cache/sessions.bak
mv ~/.cache/xfce4 ~/.cache/xfce4.bak
mv ~/.config/autostart/ ~/.config/autostart.bak
mv ~/.config/xfce4/ ~/.config/xfce4.bak
```
5. Ctrl+Alt+F7 to get back to GUI login screen and login. Those files will be replaced with the new default ones.

---

### Post by bryncoles on 2011-10-29
.... create a new user account and boot into that (all programmes will have their default settings)?

-----edit------

Toz's suggestion is cleverer than mine!  Well done Toz!

---

### Post by Ric_NYC on 2011-11-02
Thanks for the answers.

I found this way to solve it:

> How about deleting the .config/xfce4 folder under your home directory? That should reset all of your XFCE settings back to square one, and it should reinitialize on logging back in.

[http://www.reddit.com/r/linux/comments/je4o7/restore_default_xfce4_settings/](http://www.reddit.com/r/linux/comments/je4o7/restore_default_xfce4_settings/)

---

