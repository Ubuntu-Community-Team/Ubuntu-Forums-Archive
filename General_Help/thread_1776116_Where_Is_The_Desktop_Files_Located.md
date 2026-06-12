---
title: "Where Is The Desktop Files Located?"
date: 2011-06-05
forum: General Help
---

### Post by khoraski on 2011-06-05
Like

Linux Native Volume 1\Usr\Desktop\

or something...

---

### Post by lmarmisa on 2011-06-05
Your desktop files are located on

```

~/Desktop

```

The absolute path is

```

/home/yourusername/Desktop

```

This is valid for installations made in English language.

---

### Post by marcio_mi on 2011-06-05
/home/[your username]/Desktop

---

### Post by khoraski on 2011-06-05
> **lmarmisa said:**
> Your desktop files are located on

```

~/Desktop

```

The absolute path is

```

/home/yourusername/Desktop

```

This is valid for installations made in English language.

[s]Which drive? I tried the Native Volume 1 home but it says there's no recoverable files in the home folder.[/s]

Oh wait nevermind I found the drive, thanks!

---

### Post by hakermania on 2011-06-05
/home/$(logname)/Desktop/
or
/home/$USERNAME/Desktop
or
$HOME/Desktop
or
~/Desktop

All are correct, that's why I love it!

EDIT: show us your drives, it should be the one that you're using to boot ubuntu...right?

---

### Post by AlphaLexman on 2011-06-05
You shouldn't have to select which drive, it should be mounted at /home  Try this in a terminal:
```
cd ~
```

---

