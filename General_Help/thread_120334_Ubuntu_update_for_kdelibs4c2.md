---
title: "Ubuntu update for kdelibs4c2"
date: 2006-01-21
forum: General Help
---

### Post by missmoondog on 2006-01-21
Just curious as to how the update mentioned in the subject line could show up on one machine of mine and not the other (this one)? In fact, I believe there were like 3 or 4 of these updates on my other machine yesterday.

I use the gnome desktop on both machines. Have nothing kde based on either machine that I know of.

---

### Post by GeneralZod on 2006-01-21
[QUOTE=missmoondog]
Have nothing kde based on either machine that I know of.[/QUOTE]

You can test this out by doing:

```

dpkg --list | grep -i kde

```

and seeing what comes out (it outputs all packages on your system that contain the letters "KDE" in the name or description).

---

### Post by missmoondog on 2006-01-23
i'm supposed to trust a general zod?!! 

just kidding

thanks, will check it out. ;)

edit:
hmm? i've checked this on 2 of my machines. now i forgot which one had those kde updates? 3 other machines to check!

---

