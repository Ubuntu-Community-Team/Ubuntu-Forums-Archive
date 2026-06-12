---
title: "how to make terminal start at Desktop"
date: 2009-12-08
forum: General Help
---

### Post by gfunkera on 2009-12-08
my terminal starts at my user home folder, how do i make it start at my Desktop so i dont have to cd into it everytime?

---

### Post by SuperSonic4 on 2009-12-08
Have you tried looking in terminal settings for a starting directory

As a workaround you can put ```
cd Desktop
``` at the top of your .bashrc and restart your terminal. Everytime thereafter it will cd straight into Desktop

---

### Post by gfunkera on 2009-12-08
how do i look at the starting settings thing?

---

### Post by SuperSonic4 on 2009-12-08
No idea in GNOME I'm afraid, I've only ever used KDE and Openbox

---

### Post by lackoblacko on 2009-12-08
you can always create a launcher with
```

gnome-terminal --window-with-profile=<ProfileName> --execute="cd <your desktop directory>"

```
or insert your ~/.bashrc with
```

cd Desktop

```

---

### Post by prem1er on 2009-12-08
Just edit your .bashrc file as was suggested in the first response. It is the fastest and easiest way to achieve what you posted about.

---

### Post by gfunkera on 2009-12-17
where in the .bashrc file should i insert "cd Desktop"??

---

### Post by SuperSonic4 on 2009-12-17
Anywhere you like

---

