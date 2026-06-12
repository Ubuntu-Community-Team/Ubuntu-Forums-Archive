---
title: "Dwm"
date: 2011-02-23
forum: General Help
---

### Post by Ubntu on 2011-02-23
I need help with DWM. I installed it and can go into from login screen. My questions are, how can I have a transparent terminal or a theme for the terminal? Also, how can I open firefox without going into the dir. and ./firefox to open it?

---

### Post by tjwoosta on 2011-02-23
> how can I have a transparent terminal or a theme for the terminal?

That would depend which terminal your using, try google ;)

> how can I open firefox without going into the dir. and ./firefox to open it?

dmenu is a simple menu app developed by the same guys that made dwm.

---

### Post by Ubntu on 2011-02-23
> **tjwoosta said:**
> That would depend which terminal your using, try google ;)



dmenu is a simple menu app developed by the same guys that made dwm.

[I]That would depend which terminal your using, try google ;)
[/I]

The default is xterm.

*dmenu is a simple menu app developed by the same guys that made dwm.*

I'll check that out.

1/2 down just need to fix terminal.

---

### Post by tjwoosta on 2011-02-23
Afaik xterm doesnt support transparency, but you do the customizing by editing your ~/.Xdefaults

You might try urxvt, which is actually far smaller then xterm and it supports transparency. It also supports running in daemon/client mode which is great if you always have multiple instances open. Its also configured by editing ~/.Xdefaults

The fluxbox wiki has a good .Xdefaults example that should help get you going

[http://fluxbox-wiki.org/index.php?title=Xdefaults_setup](http://fluxbox-wiki.org/index.php?title=Xdefaults_setup)

And heres a thread on the arch forums that should help you figure out how to achieve transparency.
[https://bbs.archlinux.org/viewtopic.php?id=80484](https://bbs.archlinux.org/viewtopic.php?id=80484)

---

### Post by Ubntu on 2011-02-23
> **tjwoosta said:**
> Afaik xterm doesnt support transparency, but you do the customizing by editing your ~/.Xdefaults

You might try urxvt, which is actually far smaller then xterm and it supports transparency. It also supports running in daemon/client mode which is great if you always have multiple instances open. Its also configured by editing ~/.Xdefaults

The fluxbox wiki has a good .Xdefaults example that should help get you going

[http://fluxbox-wiki.org/index.php?title=Xdefaults_setup](http://fluxbox-wiki.org/index.php?title=Xdefaults_setup)

And heres a thread on the arch forums that should help you figure out how to achieve transparency.
[https://bbs.archlinux.org/viewtopic.php?id=80484](https://bbs.archlinux.org/viewtopic.php?id=80484)

Thanks for the links. I already have urxvt installed and it will not paste the code from the link you gave me. So that's making me mad. Also I can't get dmenu to work, so it is not going well.

---

