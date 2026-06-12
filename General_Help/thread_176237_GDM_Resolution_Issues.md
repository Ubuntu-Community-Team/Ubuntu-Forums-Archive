---
title: "GDM Resolution Issues"
date: 2006-05-14
forum: General Help
---

### Post by twiistedkaos on 2006-05-14
Well, I've noticed that my GDM login screen is having some resolution issues, I can't figure out where to change the resolution for it. I've checked the login settings, ect... But it doesn't seem to exist. My guess is it's using root's theme settings and display settings which is why the resolution is different compared to my desktop, now for the question 'how do I fix it' ?.

---

### Post by Maelgwyn on 2006-05-15
if you're using Gnome, 
```

sudo gedit /etc/X11/xorg.conf

```

will let you see the resolutions used.

Good luck, and hope that helps you!

---

