---
title: "Custom Ubuntu Live-cd generation with Live-helper"
date: 2010-11-14
forum: General Help
---

### Post by rhodan1 on 2010-11-14
Hello, 

I have some experience using live-helper to generate debian live-cd's, but now I need to build an Ubuntu 10.04 livecd (Lucid). 

I tried to make the live-cd using live-helper with this configuration:
Live-helper version: 2.0~a21-1
On Ubuntu Maverick

I did the following steps:
```

lh config --mode ubuntu --distribution lucid --archive-areas "main universe" --packages "make"
sudo lh build

```

this should generate a standard configuration (without any desktop environment or xorg) and i added the *make* package to the live-cd, but I got only the standard system (without make package)

What is wrong?

thanks.

pd: sorry about my english  :)

---

### Post by grubu on 2011-07-15
Hello,

maybe referring to the manpages of lh_config at:
[http://manpages.ubuntu.com/manpages/maverick/en/man1/lh_config.1.html](http://manpages.ubuntu.com/manpages/maverick/en/man1/lh_config.1.html)

would help?

Did you manage it meanwhile?

---

