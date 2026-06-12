---
title: "zsh aliases"
date: 2009-08-04
forum: General Help
---

### Post by Qvintvs on 2009-08-04
In my .zshrc file, I've alised emacs as 'emacs -nw'. This works fine normally, but not with sudo. 'sudo emacs some_file' still opens with the gtk frontend. I tried adding the alias to the root account's .zshrc, but sudo still doesn't seem to recognize the alias. does anyone know of a way to get the alias to work with sudo?

---

### Post by sisco311 on 2009-08-04
you can use a global alias:
```
alias -g emacs='echo use vim && emacs -nw'
```
:evil:

EDIT: or simply:

```
alias -g emacs='emacs -nw'
```
:)

---

### Post by Qvintvs on 2009-08-04
you mean alias -g emacs='echo emacs is teh wins && emacs -nw', right?

hehe...anyway, thx, that did it.

---

### Post by sisco311 on 2009-08-04
> **Qvintvs said:**
> you mean alias -g emacs='echo emacs is teh wins && emacs -nw', right?

hehe...anyway, thx, that did it.

:)

unfortunately, the global alias is not the optimal solution.

i.e.:
```
nano emacs
```
will open the file "emacs" and the file "-nw" 

see:
[https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/275713]("https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/275713")

the workaround works in zsh as well:
```
alias emacs='emacs -nw'
alias sudo='A=`alias` sudo '
```

---

### Post by Qvintvs on 2009-08-04
hm... interesting. what exactly is the A= for? is just so that the output of `alias` is sent somewhere instead of being interpreted? also... it doesn't seem to work without the trailing space... why is that?

---

### Post by sisco311 on 2009-08-04
> **Qvintvs said:**
> hm... interesting.
yep, it is.

from man alias:
> 4. Set up nohup so that it can deal with an argument that is itself an
           alias name:

           alias nohup="nohup "



now i understand why alias sudo='sudo ' works. 


A=`alias` assigns the output of "alias" to the A environment variable, but i don't know why this is needed.

i'm tired, i will investigate this tomorrow.

---

### Post by Qvintvs on 2009-08-04
just having alias sudo='sudo ' (instead of alias sudo='A=`alias` sudo ') seems to work fine, though I'm still not clear on what the space is doing...

---

### Post by bodhi.zazen on 2009-08-04
You can also add the alias to root (since sudo uses root's .bashrc).

the -e flag may also work

alias foo='sudo -E emacs -nw'

---

### Post by sisco311 on 2009-08-05
> **bodhi.zazen said:**
> You can also add the alias to root (since sudo uses root's .bashrc).


.bashrc is not sourced by default.

login-specific resource files such as.profile or .login are sourced if an initial login is simulated (sudo -i)


> **Qvintvs said:**
> hm... interesting. what exactly is the A= for? is just so that the output of `alias` is sent somewhere instead of being interpreted? 


I don't know. It makes no sense at all.
Just use *alias sudo='sudo '*

> **Qvintvs said:**
> 
also... it doesn't seem to work without the trailing space... why is that?

If the last  character  of  the  alias value is a blank, then the next command word following the alias is also checked for alias expansion.

---

