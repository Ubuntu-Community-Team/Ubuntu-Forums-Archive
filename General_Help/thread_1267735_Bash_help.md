---
title: "Bash help"
date: 2009-09-16
forum: General Help
---

### Post by tempfolder on 2009-09-16
Hi,

How do I make bash recognize an executable regardless of current directory? For example, typing "firefox" in terminal opens firefox without the need to go to /usr/lib/firefox-3.0.14/.

Thanks.

---

### Post by nothingspecial on 2009-09-16
Put the executable in /usr/bin/

---

### Post by tempfolder on 2009-09-16
> **nothingspecial said:**
> Put the executable in /usr/bin/

The executable must stay in its current directory. Is there another way of doing this?

---

### Post by nothingspecial on 2009-09-16
Scrub that
```

export PATH=$PATH:directory
```

---

### Post by tempfolder on 2009-09-16
> **nothingspecial said:**
> Put the directory in your path.
```

PATH=where/it/is:”${PATH}”
```

is there a way to make this permanent and not just the current instance of terminal?

btw: is Terminal the same thing as Bash?

---

### Post by tempfolder on 2009-09-16
> **nothingspecial said:**
> Scrub that
```

export PATH=$PATH:directory
```

same question - how can i make this permanent?

---

### Post by lvlint67 on 2009-09-16
> **tempfolder said:**
> is there a way to make this permanent and not just the current instance of terminal?

btw: is Terminal the same thing as Bash?

Setting the path in bash:
[http://ubuntuforums.org/showthread.php?t=317070](http://ubuntuforums.org/showthread.php?t=317070)

---

### Post by nothingspecial on 2009-09-16
Yep you need to edit your .bashrc

---

### Post by tempfolder on 2009-09-16
awesome, thanks!

---

### Post by KiLaHuRtZ on 2009-09-16
To make it permanent...

```
echo "PATH=$PATH:/my/dir1:/my/dir2:/my/dir3" >> ~/.bashrc
echo "PATH=$PATH:/my/dir1:/my/dir2:/my/dir3" >> ~/.bash_profile
```

To refresh, simply logout and log back in, or do the following...

```
. ~/.bashrc
```

---

### Post by geirha on 2009-09-16
> **tempfolder said:**
> btw: is Terminal the same thing as Bash?

Strictly speaking they are two separate programs, see [http://en.wikipedia.org/wiki/Terminal_emulator](http://en.wikipedia.org/wiki/Terminal_emulator). Bash just happens to be the program started in a terminal emulator by default on Ubuntu and many other linux distros, but you could just as well run any other textual program instead of bash.

---

