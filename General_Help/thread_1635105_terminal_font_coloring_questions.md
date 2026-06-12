---
title: "terminal font coloring questions"
date: 2010-12-01
forum: General Help
---

### Post by I'mGeorge on 2010-12-01
Ok I want the username and OS specified in the terminal to look something like this

```

**[COLOR="Red"]username[/COLOR][COLOR="RoyalBlue"]@ubuntu:~$[/COLOR][COLOR="Silver"]apt-get moo[/COLOR]**

```

can this be done in xterm or aterm or any other terminal for that matter ?

---

### Post by TeoBigusGeekus on 2010-12-01
```
PS1="\033[0;31m\u\033[0;34m@\h:\w\$\033[0m"
export PS1
```

---

### Post by I'mGeorge on 2010-12-01
> **TeoBigusGeekus said:**
> ```
PS1="\033[0;31m\u\033[0;34m@\h:\w\$\033[0m"
export PS1
```

Thx man, now my terminal blends a little bit better into my desktop theme.

---

### Post by 0949er on 2010-12-01
> **TeoBigusGeekus said:**
> ```
PS1="\033[0;31m\u\033[0;34m@\h:\w\$\033[0m"
export PS1
```

how did you come up with that? for those of us who want to create our own custom string?

and is that a permanent change or does it default back to normal once restarted?

---

### Post by TeoBigusGeekus on 2010-12-01
> **0949er said:**
> how did you come up with that? for those of us who want to create our own custom string?

and is that a permanent change or does it default back to normal once restarted?

[http://sourceforge.net/projects/linuxcommand/files/TLCL/09.12/TLCL-09.12.pdf/download]("http://sourceforge.net/projects/linuxcommand/files/TLCL/09.12/TLCL-09.12.pdf/download")
Chapter 14

---

### Post by I'mGeorge on 2010-12-01
> **0949er said:**
> how did you come up with that? for those of us who want to create our own custom string?

and is that a permanent change or does it default back to normal once restarted?

Nice manual @TeoBigusGeekus but to answer @0949er in a few words here it goes.
PS1 it's a shell variable, as I've just found out myself. So if you wanna find more about how you can customize prompt settings that are stored in this variable,and it's parameters follow this link [http://www.cyberciti.biz/faq/bash-shell-change-the-color-of-my-shell-prompt-under-linux-or-unix/](http://www.cyberciti.biz/faq/bash-shell-change-the-color-of-my-shell-prompt-under-linux-or-unix/)

If you wanna make the changes permanent edit the file ~/.bashrc from your home folder. Look for something that's pretty much like this

```

PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"

```

and replace it with your own, in my case it's what TeoBigusGeekus already gave me

```

PS1="\033[0;31m\u\033[0;34m@\h:\w\$\033[0m"

```

---

