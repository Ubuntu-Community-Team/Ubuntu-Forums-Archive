---
title: "Wine libjack.so problem"
date: 2006-06-13
forum: General Help
---

### Post by jarg on 2006-06-13
When I run winecfg and move to the audio table I get this error.
```
jared@ubuntu:~$ winecfg
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack
```
I searched the forums but found nothing that would solve my problem, I found many unsolved posts.

---

### Post by buzux on 2006-09-08
Hi,

sudo apt-get install libjack0.100.0-0
sudo ln -sf /usr/lib/libjack-0.100.0.so.0 /usr/lib/libjack.so

and it works.

I am under Ubuntu Dapper + Wine 0.9.19.
Hope I helped you.

---

### Post by dimis on 2006-09-25
> **buzux said:**
> ```
sudo apt-get install libjack0.100.0-0
sudo ln -sf /usr/lib/libjack-0.100.0.so.0 /usr/lib/libjack.so
```
I just report that this didn't work for me. I still have the same problem as jarg. However, this is the second day of me experiencing wine, so ... any more thoughts are more than welcome. :)

Thank you in advance for your time,
- dimis -

---

### Post by Aurora on 2006-11-12
I see this thread is getting stale, but for the record:

After checking to find libjack-0.1000.0.so.0 already installed,

me@mycomputer:~$ sudo ln -sf /usr/lib/libjack-0.1000.0.so.0 /usr/lib/libjack.so
me@mycomputer:~$ winecfg
/bin/sh: /usr/bin/esd: No such file or directory
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack

---

### Post by scrooge_74 on 2006-11-12
I did worked for me link was created no problem

---

### Post by Scrappy_D on 2006-11-14
Shouldn't that command look like this?
 sudo ln -s /usr/lib/libjack-0.100.0.so.0 /usr/lib/wine/libjack.so


:)

---

### Post by scrooge_74 on 2006-11-14
> **Scrappy_D said:**
> Shouldn't that command look like this?
 sudo ln -s /usr/lib/libjack-0.100.0.so.0 /usr/lib/wine/libjack.so


:)

It should also work, unless you need to remove an existing file so you only end up with what you just installed.

It does work the message dissapear and in the audio tab in winecfg the lib jack is listed

---

