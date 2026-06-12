---
title: "Create a shortcut in Server 12.04"
date: 2012-10-10
forum: General Help
---

### Post by cb46 on 2012-10-10
I was trying to find out how to create a shortcut from command line. Basically so when I log in I can get straight to a directory I need instead of typing /my/files/located/down/here, it would just be /myfiles. Still a little noobish so any help would be great.

---

### Post by sienile on 2012-10-10
Not sure how to do it from the command line, but you can do it from a file manager. In Linux, symbolic links are used in place of shortcuts. It's pretty much the same thing, but better.

I don't use the default file manager, but in Krusader it's as easy as drag and drop, then select "Link Here".

---

### Post by BrandonIngalls on 2012-10-10
You can create a symbolic link...
```
ln -s ~/path/to/thing shortcutName
```

Then you cd into shortcutName you will be in ~/path/to/thing

---

### Post by cb46 on 2012-10-10
> **BrandonIngalls said:**
> You can create a symbolic link...
```
ln -s ~/path/to/thing shortcutName
```

Then you cd into shortcutName you will be in ~/path/to/thing
Thank you Brandonlngalls, that worked great :)

---

### Post by dcstar on 2012-10-11
> **cb46 said:**
> Thank you Brandonlngalls, that worked great :)

Then **MARK** the thread.

---

