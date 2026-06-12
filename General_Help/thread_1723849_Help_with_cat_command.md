---
title: "Help with cat command"
date: 2011-04-07
forum: General Help
---

### Post by spiky001 on 2011-04-07
Hi just a simple question if I use "cat" to make a file, it will make it in the dir I am in. Is it possible to "cat" the file to another dir if so how?

---

### Post by TeoBigusGeekus on 2011-04-07
Try with touch
```
touch /path/nameoffile
```

If you want to use cat, then
```
cat > /path/nameoffile
```

---

### Post by spiky001 on 2011-04-07
Thks

---

### Post by WorMzy on 2011-04-07
If you use the second example, remember to end your input with Ctrl+D, and not Ctrl+C.

e.g.
```
cat > /path/nameoffile
This text is entered into the file.
[COLOR="Red"]Ctrl+D[/COLOR]
```

---

### Post by spiky001 on 2011-04-07
Thks I just couldn't get it to another dir but thks for reminder

---

