---
title: "jobs manpage missing"
date: 2010-11-30
forum: General Help
---

### Post by COKEDUDE on 2010-11-30
Could anyone explain why my jobs manpages are missing? I noticed that there is Ubuntu manpage entry. 

[http://manpages.ubuntu.com/cgi-bin/search.py?q=jobs&op=&cx=003883529982892832976%3A5zl6o8w6f0s&cof=FORID%3A9&ie=UTF-8&siteurl=manpages.ubuntu.com%2F](http://manpages.ubuntu.com/cgi-bin/search.py?q=jobs&op=&cx=003883529982892832976%3A5zl6o8w6f0s&cof=FORID%3A9&ie=UTF-8&siteurl=manpages.ubuntu.com%2F)

Also when I check on various Linux systems it takes me to BASH_BUILTINS(1). I also can't seem to find BASH_BUILTINS(1) on my system either.

---

### Post by luigi_mb on 2010-11-30
In a console, try

```

help jobs

```

/luigi

---

### Post by COKEDUDE on 2010-12-02
Thank you. I didn't even think about that command.

---

### Post by Habitual on 2010-12-02
```
info jobs
```
too!

---

### Post by gmargo on 2010-12-02
> **COKEDUDE said:**
> Could anyone explain why my jobs manpages are missing? .....

Also when I check on various Linux systems it takes me to BASH_BUILTINS(1). I also can't seem to find BASH_BUILTINS(1) on my system either.

**jobs** is a function built into the **bash** shell.  It is documented both in the **bash(1)** and **bash-builtins(7)** man pages.  (Note use of dash, not underscore, for bash-builtins.)

---

### Post by COKEDUDE on 2010-12-03
> **gmargo said:**
> **jobs** is a function built into the **bash** shell.  It is documented both in the **bash(1)** and **bash-builtins(7)** man pages.  (Note use of dash, not underscore, for bash-builtins.)

What??

> Also when I check on **various Linux systems** it takes me to BASH_BUILTINS(1). I also can't seem to find BASH_BUILTINS(1) on my system either.

I said on various Linux systems.

---

