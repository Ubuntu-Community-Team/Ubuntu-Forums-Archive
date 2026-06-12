---
title: "I killed compiz"
date: 2009-10-28
forum: General Help
---

### Post by Jeffonfire on 2009-10-28
I set compiz for more than my computer's hardware can handle and now it causes the screen to have black splotches over the windows. How can I lower my compiz settings through the comand line?

---

### Post by dbyjazz on 2009-10-28
> **Jeffonfire said:**
> I set compiz for more than my computer's hardware can handle and now it causes the screen to have black splotches over the windows. How can I lower my compiz settings through the comand line?

one way..

```
sudo apt-get remove compiz
```

then reinstall

```
sudo apt-get install compiz
```

---

### Post by razorboy5 on 2009-10-28
+1 to above post

not 100% sure when u reinstall the setting might be the same as when uninstalled

so set ur visual settings to none then install it and lower the setting then turn it back on to extras afterwards

---

### Post by TheForumTroll on 2009-10-29
If you can get to it you can set compiz to defaults in CompizConfig Settings Manager.

---

### Post by Jeffonfire on 2009-10-29
Yea, I can't get to the CompizConfig Settings Manager because my screen is black over the windows. I will try to reinstall it though.

---

### Post by cipicip on 2009-10-29
> **razorboy5 said:**
> +1 to above post

not 100% sure when u reinstall the setting might be the same as when uninstalled

so set ur visual settings to none then install it and lower the setting then turn it back on to extras afterwards

Or you can do:
```
sudo apt-get purge compiz
```
and
```
sudo apt-get install compiz
```

This will erase all settings related to compiz.

---

### Post by Jeffonfire on 2009-10-29
Well, I tried to purge it, reinstall it, remove it. It is still having the same problem. It could be a problem with me setting the ubuntu native graphics quality settings. I set them on high before the problem started. How do I reset that?

---

### Post by Jeffonfire on 2009-10-30
I am really lost. :( if someone has any idea how to fix this please post!

---

### Post by kimberlite on 2009-10-30
Maybe reconfiguring X can help you:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

