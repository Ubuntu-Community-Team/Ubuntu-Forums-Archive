---
title: "about man"
date: 2010-03-14
forum: General Help
---

### Post by benzfish on 2010-03-14
Hello, everybody. There is a question for me. I want to use "man" to see declaration of "c function", so I used command > apt-get install manpages-dev to add man pages to my ubuntu.Then, I can use > man -f system to see which command system I can check, and the result is like as follow:
> 
system (3)           - execute a shell command
system (3posix)      - issue a command
ok, if I use 
> man system
then the default man page is about system (3) but, I want to see system (3posix), so I input 
> man system (3posix)
then there is a error
> bash: syntax error near unexpected token `('

How can I see system (3posix), and why this error happened? Thank you!

---

### Post by srs5694 on 2010-03-15
Try:

```

man 3posix system

```

---

### Post by benzfish on 2010-03-15
> **srs5694 said:**
> Try:

```

man 3posix system

```

Thanks, srs5694. You are right...Thank you very much!

---

