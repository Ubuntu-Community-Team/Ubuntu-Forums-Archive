---
title: "Ubuntu doesn't start after login"
date: 2009-11-23
forum: General Help
---

### Post by viren.ec on 2009-11-23
Hi, 
I am using ubuntu 8.04.
It got hanged while I was changing the GTK-2.0 themes.
So,I Restart the laptop, but after that It hangs just after login.

I don't know why it hanged before.
Is there any way to get recovery or something like that?

Thanks in advance.

---

### Post by Giblet5 on 2009-11-23
You installed a theme that does not work.

Print these directions and follow them. PAY CAREFUL ATTENTION TO THE FILENAMES - THEY HAVE '.'s AT THE BEGINNING.


Flip to the console via Ctrl+Alt+F1.

Log in.

Run these commands:

```
mkdir dotback
mv .gconf* .config dotback
exit
```

Flip back to graphics mode via Ctrl+Alt+F7.

Log in.

All of your display settings should be the Ubuntu defaults. You'll have to set a few things up again (email, IM, etc) but at least it works.

You have a complete backup of your old settings in $HOME/dotback, if you want to try and figure out what went wrong.

---

### Post by viren.ec on 2009-11-25
Hey thanks,

I have moved my old configuration, and now it starts normally.
You were right it was the unsupported theme Ihave installed.

---

