---
title: "How to add a command to sudo"
date: 2011-03-27
forum: General Help
---

### Post by banff2010 on 2011-03-27
I have downloaded a tar ball and installed a program. This program needs root privilege  to run. Say the command is nxt. The nxt has an option ERASE How do I make so that it runs as
```
 sudo nxt ERASE
``` I have set up root password and everything, but don't know how to do it.

---

### Post by NuMPTy_87 on 2011-03-27
Just to clarify - are you going to be running the command every time you launch the program, or do you want it to execute automagically with root privileges?

IE every time you want to use 'nxt ERASE' you just don't want to type 'sudo' first?

---

### Post by banff2010 on 2011-03-27
I want  it to execute automatically with root privileges.  How would I do that?

Thanks.

---

### Post by d3v1150m471c on 2011-03-27
```

sudo ./configure
sudo make
sudo make install

```since you're running source code on a ".deb" machine, you should check out checkinstall.

furthermore:
```

#you can append everything to sudo
sudo echo 'pizza pizza!' | sed 's/\(.\)\(.\)/\u\1\2/g'

```

---

### Post by fela on 2011-03-27
Edit ~/.bashrc:

Where it has all the aliases (such as alias ll="ls -al"), add:

alias nxt="sudo nxt"

---

