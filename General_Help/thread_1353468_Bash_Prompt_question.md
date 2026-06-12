---
title: "Bash Prompt question"
date: 2009-12-12
forum: General Help
---

### Post by nmaster on 2009-12-12
Hi all,

I recently changed my bash prompt in .bashrc.    
```
PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w \n$ '

```

As a result, my prompt looks like this:
```

neal@neal-laptop:~ 
$ emacs .bashrc
neal@neal-laptop:~ 
$ 

```

This is almost what I want.  How do I change it so that instead of ~ it shows /home/neal?  I'd like my prompt to look like this:
```

neal@neal-laptop:/home/neal/
$ 

```

I still want '~' to be be shorthand for my home folder, I'd just don't want any shorthand in the prompt.  I don't really know much about editing my .bashrc file besides setting aliases.  I kind of guessed a few times and got lucky with the small change I did make.  

Thanks for the help!

---

### Post by diesch on 2009-12-12
```
'${debian_chroot:+($debian_chroot)}\u@\h:$PWD \n$ '
```

---

### Post by nmaster on 2009-12-12
sweet! thanks.

---

