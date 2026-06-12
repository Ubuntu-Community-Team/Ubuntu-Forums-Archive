---
title: "pidgin crash"
date: 2012-09-05
forum: General Help
---

### Post by micahpage on 2012-09-05
I didnt have any problems untill i rebooted my pc:

i started up pidgin and it will give me the screen for a bit, and then it will disappear. So i tried it in the terminal, and this is the error i get.
Does anyone know how to fix this?

```
metulburr@ubuntu:~$ pidgin
Pidgin: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
metulburr@ubuntu:~$
```

>  DISTRIBUTION:  Ubuntu 12.04.1 LTS precise
      DESKTOP:  GNOME
       KERNAL:  3.2.0-29-generic
          BIT:  64
          CPU:  Intel(R) Core(TM) i7-2600 CPU @ 3.40GHz [8] Core
    PARTITION:  146 / 210 GB
          RAM:  1279 / 7967 MB


I came across an old thread with related problems that suggested:
```
$ xhost +

```
I'm not usre exactly what that does, but i tried it and it still gets the same error.

---

