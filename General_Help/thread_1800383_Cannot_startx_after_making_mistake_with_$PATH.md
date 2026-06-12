---
title: "Cannot startx after making mistake with $PATH"
date: 2011-07-08
forum: General Help
---

### Post by buffalo960 on 2011-07-08
I recently made a mistake and made my PATH variable nothing. I didn't notice this problem until I rebooted my computer and it would not let me login (the normal graphical login). I went into the terminal and found that my PATH variable was wrong so I edited my .bashrc file, adding ```
export PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```

this seemed to fix the problem in the terminal now I can access all of the binaries normally, but I still can login with the graphical login and I still cant startx.

Thanks for you help

---

### Post by bodhi.zazen on 2011-07-08
That path looks fine. Either log out or reboot or post any error messages you are getting when you startx in a terminal.

---

