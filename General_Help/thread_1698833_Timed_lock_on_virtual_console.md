---
title: "Timed lock on virtual console"
date: 2011-03-02
forum: General Help
---

### Post by jwbrase on 2011-03-02
Something I find myself doing every once in a while is using Ctrl-Alt-F[x] to switch out to a virtual terminal, and the Alt-F7-ing back to X without logging out.

While I don't anticipate that too many people that might have access to my computer would know how to switch consoles, there is still some degree of security risk provided by a logged-in console session. I've found [vlock]("http://manpages.ubuntu.com/manpages/maverick/man1/vlock.1.html"), but that seems to lock the console immediately when called, rather than running as a daemon that locks inactive consoles. (Even it's -t option just gives a timeout before an optional (and separate) text-mode screensaver package activates, rather than an inactivity timeout).

Is there any vlock-like package out there that provides the timed locking services for text consoles that XScreenSaver provides for X? Either a lock on timeout or a lock on switchaway setup would be adequate.

---

### Post by jerome1232 on 2011-03-02
I know byobu can do that, it's a screen like utility that comes with 10.10,

if it's not installed install it, you can configure it to auto-run when you get into a virutal terminal with dpkg

```
sudo dpkg-reconfigure byobu
```

after installing get into a virtual terminal and hit F9 to peruse it's menu's, in there is an option to auto lock.

edit: Correction, if you press F12 it locks, I was wrong about But you can set it to auto lock per the first comment on this bug report

[https://bugs.launchpad.net/byobu/+bug/553086](https://bugs.launchpad.net/byobu/+bug/553086)

---

### Post by jwbrase on 2011-03-02
> **jerome1232 said:**
> I know byobu can do that, it's a screen like utility that comes with 10.10,

I'm using 10.04, but it is on my system. The package description says it's a set of profiles for screen, not just a "screen like" utility.

Thanks...

---

### Post by jerome1232 on 2011-03-03
Your right, I actually just found that little program like 5 minutes before I stumbled on your thread and realized that it was just profiles for screen when I saw the reference to .screenrc in that bug report.

I certainly like it and I hope it works for you though.

---

### Post by pathakvirendra on 2011-07-19
[B]I  have disabled direct root login ( sudo passwd -dl root) on ubuntu  server 11.04 . To lock virtual console I am using vlock. Now if I lock  entire virtual console (vlock -n ) and to unlock it i enter root  password , it say root Authentication failed !!!!!!!!!
Is dere any way to use vlock facility even after disabling direct root login??? Plz help[/B]

---

