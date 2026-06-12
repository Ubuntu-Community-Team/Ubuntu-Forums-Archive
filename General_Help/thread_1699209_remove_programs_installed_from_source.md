---
title: "remove programs installed from source?"
date: 2011-03-03
forum: General Help
---

### Post by sr_guy on 2011-03-03
Running 10.10 64bit

I tried installing the latest Mupen64Plus from source, and something went wrong, and now I get errors when trying to run it. How do I remove the link that was created from the source install?

This is what I get:

|  \/  |_   _ _ __   ___ _ __  / /_ | || | |  _ \| |_   _ ___
| |\/| | | | | '_ \ / _ \ '_ \| '_ \| || |_| |_) | | | | / __|
| |  | | |_| | |_) |  __/ | | | (_) |__   _|  __/| | |_| \__ \
|_|  |_|\__,_| .__/ \___|_| |_|\___/   |_| |_|   |_|\__,_|___/
             |_|         [http://code.google.com/p/mupen64plus/](http://code.google.com/p/mupen64plus/)
Mupen64Plus Console User-Interface Version 1.99.4

dlopen('./libmupen64plus.so.2') error: ./libmupen64plus.so.2: cannot open shared object file: No such file or directory
AttachCoreLib() Error: failed to find Mupen64Plus Core library


I just want to remove it totally and install from a PPA source

---

### Post by gandaran on 2011-03-03
> **sr_guy said:**
> Running 10.10 64bit

I tried installing the latest Mupen64Plus from source, and something went wrong, and now I get errors when trying to run it. How do I remove the link that was created from the source install?

This is what I get:

|  \/  |_   _ _ __   ___ _ __  / /_ | || | |  _ \| |_   _ ___
| |\/| | | | | '_ \ / _ \ '_ \| '_ \| || |_| |_) | | | | / __|
| |  | | |_| | |_) |  __/ | | | (_) |__   _|  __/| | |_| \__ \
|_|  |_|\__,_| .__/ \___|_| |_|\___/   |_| |_|   |_|\__,_|___/
             |_|         [http://code.google.com/p/mupen64plus/](http://code.google.com/p/mupen64plus/)
Mupen64Plus Console User-Interface Version 1.99.4

dlopen('./libmupen64plus.so.2') error: ./libmupen64plus.so.2: cannot open shared object file: No such file or directory
AttachCoreLib() Error: failed to find Mupen64Plus Core library


I just want to remove it totally and install from a PPA source
did you use make and make install for installing or something else? if correct then you have to 'make' the package again but instead typing 'make install' (or sudo make install) you type 'make uninstall', that should remove completely the program.

---

### Post by seawolf167 on 2011-03-03
In the future, you may want to consider [checkinstall ]("http://www.asic-linux.com.mx/%7Eizto/checkinstall/")for ease of removing source-installed packages

```
sudo apt-get install checkinstall
```

---

