---
title: "how can i know the name of an app that is running?"
date: 2009-09-26
forum: General Help
---

### Post by chriskin on 2009-09-26
if an app is running on my desktop, how can i know the exact name the OS uses to refer to it?
i want to find the name the fullscreen mode of Vlc has, as i have compiz on transparency on all applications except those i choose.

vlc and vlc's fullscreen seem to have differenet names - it also seems that i cannot click on vlc's fullscreen with compiz's grab tool to get the name

EDIT : putting & !(state=fullscreen) at compiz transparency list will make All fullscreen applications not transparent, video-related ones as well :)

since i use no other apps at fullscreen other than those i want to be non-transparent, this option works perfectly for me

credit goes to Frank64 of the compiz fusion forums, at the first post of [http://forum.compiz-fusion.org/showthread.php?t=2388&page=3](http://forum.compiz-fusion.org/showthread.php?t=2388&page=3)

---

### Post by MelDJ on 2009-09-26
add and open system monitor from the panel

---

### Post by chriskin on 2009-09-26
> **MelDJ said:**
> add and open system monitor from the panel

i tried that too, i cann't find anything that would seem to be vlc's fullscreen

---

### Post by MelDJ on 2009-09-26
how about: ps -A or top in terminal

---

### Post by ecmatter on 2009-09-26
Check the man page:

```

man vlc

```

> 
OPTIONS
VLC  follows  the  usual  GNU command line syntax, with long options starting with two dashes (‘-’).  For a precise description of options, please use "vlc --help".

The complete list of VLC options depends on what plugins are installed because they  automatically  add  their  own options. Please use "vlc --longhelp --advanced" for a complete list of available options.


```

vlc --help

```

> 
-f, --fullscreen, --no-fullscreen
        Fullscreen video output (default disabled)


So, to open a video file in fullscreen mode:

```

vlc --fullscreen path/to/file

```

-or-

```

vlc -f path/to/file

```

Wherever you're adding exceptions in Compiz, you should add the following:

```

vlc --fullscreen

```

---

### Post by NoaHall on 2009-09-26
It's just vlc.

---

### Post by chriskin on 2009-09-28
> **NoaHall said:**
> It's just vlc.

no it's not :P

---

### Post by chriskin on 2009-09-28
> **ecmatter said:**
> Check the man page:

```

man vlc

```



```

vlc --help

```



So, to open a video file in fullscreen mode:

```

vlc --fullscreen path/to/file

```

-or-

```

vlc -f path/to/file

```

Wherever you're adding exceptions in Compiz, you should add the following:

```

vlc --fullscreen

```

thank you, i'm trying it right now

edit : didn't work

---

### Post by grturner on 2009-09-28
ps aux | grep vlc
or 
top

run both in terminal

---

### Post by chriskin on 2009-09-28
> **grturner said:**
> ps aux | grep vlc
or 
top

run both in terminal

nothing shows up
i think i found something on compiz's forums, so it's ok

---

### Post by Rytron on 2009-09-28
Try ```
htop
```

---

### Post by chriskin on 2009-09-28
> **Rytron said:**
> Try ```
htop
```

this was said more than once, nothing vlc related pops up.
the solution to the problem is on first post for anyone who cares

---

