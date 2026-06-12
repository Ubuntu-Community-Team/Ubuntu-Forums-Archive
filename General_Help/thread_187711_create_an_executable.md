---
title: "create an executable"
date: 2006-06-03
forum: General Help
---

### Post by frizzl on 2006-06-03
in another thread, a guide says to 'chmod+x or chmod 775' the file, to make it an executable.

HOW exactly is this done?

thankyou all very much :)

---

### Post by mbirkis on 2006-06-03
[QUOTE=frizzl]in another thread, a guide says to 'chmod+x or chmod 775' the file, to make it an executable.

HOW exactly is this done?

thankyou all very much :)[/QUOTE]

open up the terminal, run: chmod 775 /location/to/file/filename

---

### Post by taurus on 2006-06-03
Open a terminal by clicking Applications -> Accessories -> Terminal.  Then, assuming that you are the owner of the file, type
```

chmod 755 <filename>

```
But if you are not the owner of the file, then do
```

sudo chmod 755 <filename>

```

---

### Post by soze on 2006-06-03
[QUOTE=mbirkis]open up the terminal, run: chmod 775 /location/to/file/filename[/QUOTE]

Or, if you are GUI-inclined right-click on the file in Nautilus, select "Properties" click on the "permissions" tab and then tick the appropriate box.

---

### Post by cgjones on 2006-06-05
What are you trying to execute?

---

