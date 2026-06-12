---
title: "Compiling error - No package 'x11' found"
date: 2011-09-13
forum: General Help
---

### Post by wadd92 on 2011-09-13
Full error

No package 'x11' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables X11_CFLAGS
and X11_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


I am getting this while trying to install Alian Arena. I'm still new to Ubuntu and have tried searching here and on google and couldn't find anything so forgive me if this is a nooby question which has been answered before. I am btw running Ubuntu 11.04

---

### Post by WorMzy on 2011-09-13
Do you have a specific reason for not installing it from the repos?

```
sudo apt-get install alien-arena
```

If you want to compile it, I believe you can get past that error message by installing libx11-dev.

```
sudo apt-get install libx11-dev
```

---

### Post by wadd92 on 2011-09-13
> **WorMzy said:**
> Do you have a specific reason for not installing it from the repos?

```
sudo apt-get install alien-arena
```

If you want to compile it, I believe you can get past that error message by installing libx11-dev.

```
sudo apt-get install libx11-dev
```

Thanks it worked, and I prefer downloading larger files such as this game mainly due to being a Windows user for so long, downloading and then installing is what I'm used to

---

