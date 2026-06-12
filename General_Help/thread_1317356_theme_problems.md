---
title: "theme problems"
date: 2009-11-06
forum: General Help
---

### Post by Naegling23 on 2009-11-06
I upgraded to 9.10

everytime I log in, my theme is gone, once I go to system>preferences>Appearance, it magically appears.  However, sometimes nautilus is not themed, no matter what I do.

So, how do I fix both of these problems, what is going on?

---

### Post by Giblet5 on 2009-11-06
Make sure the permissions are correct:

```
sudo find $HOME/.config $HOME/.gconf* -type d -exec chmod 750 {} \; -exec chown $LOGNAME:$LOGNAME {} \;
sudo find $HOME/.config $HOME/.gconf* -type f -exec chmod 640 {} \; -exec chown $LOGNAME:$LOGNAME {} \;
```

Now try setting your themes, logging off, then logging back in.

It *should* be correct now.

---

### Post by Naegling23 on 2009-11-08
that doesnt solve the problem.

However, I noticed that this only occurs with certain themes, and I think that might be where the problem is.  I had dust installed prior to 9.10, and as I understand it, dust is now one of the official themes.  Well, when I select dust, at login, I loose the theme.  However, I installed some custom themes after 9.10 (this was after the problem occured btw), and they work just fine.  So it might not be a system wide problem, but a dust problem.....is there a way to uninstall/reinstall select themes?

---

### Post by Naegling23 on 2009-11-09
I removed and reinstalled the dust themes, but the problem persists, and it only seems to be them.

---

### Post by SerafeimG on 2009-11-15
Same problem here
I don't know what caused it but with this two command lines the problem where solved. Everything is ok!

Many thanks to Giblet5

---

