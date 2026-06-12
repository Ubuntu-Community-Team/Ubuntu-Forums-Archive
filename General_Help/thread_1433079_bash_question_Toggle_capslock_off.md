---
title: "bash question: Toggle capslock off?"
date: 2010-03-18
forum: General Help
---

### Post by anarkhos on 2010-03-18
I understand how to *deactivate* capslock:
[http://www.peterbe.com/plog/blogitem-041021-1?msg=Comment+added!&r=823s#c100318ibvt](http://www.peterbe.com/plog/blogitem-041021-1?msg=Comment+added!&r=823s#c100318ibvt)

... but, I don't want to deactivate it.  I want to be able to *toggle* it off, but allow capslock to still be useable.

For instance, I would make an alias to `LS`, so that it would toggle capslock off, then send the command `ls`.  I'd do the same for `CD`.

Any ideas?

---

### Post by Seq on 2010-03-18
Hmmm. It seems you could use `setleds -caps`, but that only works on a console, not within X. I couldn't find an equivilant to `numlockx` for toggling the caps-lock.

---

### Post by anarkhos on 2010-03-25
> **Seq said:**
> Hmmm. It seems you could use `setleds -caps`, but that only works on a console, not within X. I couldn't find an equivilant to `numlockx` for toggling the caps-lock.

hmmm.. I tried this in bash, and got the following error:

```
gavin@gavin-ubuntu-work:~$ setleds -caps
KDGKBLED: Invalid argument
Error reading current flags setting. Maybe you are not on the console?

```

I am confused, because I thought bash *was* the console!

---

### Post by Seq on 2010-03-25
> **anarkhos said:**
> hmmm.. I tried this in bash, and got the following error:

```
gavin@gavin-ubuntu-work:~$ setleds -caps
KDGKBLED: Invalid argument
Error reading current flags setting. Maybe you are not on the console?

```

I am confused, because I thought bash *was* the console!

Bash is just a shell, you're running it in gnome-terminal, right?

Consoles are what you get when you don't have a graphical environment. Text-only. Press CTRL+ALT+F1 to see one. CTRL+ALT+F7 to get back.

---

### Post by anarkhos on 2010-03-25
very interesting, thank you.

---

