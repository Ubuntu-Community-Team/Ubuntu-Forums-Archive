---
title: "Top &amp; Bottom panel gone missing"
date: 2010-08-14
forum: General Help
---

### Post by [Shawn] on 2010-08-14
I just restarted my computer to come back to no top and bottom panels. I don't have Maximize Minimize or Close buttons at the top of the windows either! How can I restore the buttons and the panels? :confused:

---

### Post by corrytonapple on 2010-08-16
There may be a check in the Assistive Technologies box for enabling them. (First check box in that window.) Get the panels back by right clicking the desktop and clicking create launcher I think. See if that works.

---

### Post by Ginsu543 on 2010-08-16
Are you running Compiz by any chance? I get those same symptoms when my Compiz goes on the fritz. Try opening Terminal and type:
```

metacity --replace

```This will change your window manager to metacity. See if this will bring your panels and window trimming back.

If you want to turn Compiz back on, type:
```

compiz --replace

```

---

