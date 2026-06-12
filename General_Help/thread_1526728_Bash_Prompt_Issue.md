---
title: "Bash Prompt Issue"
date: 2010-07-08
forum: General Help
---

### Post by adamcole83 on 2010-07-08
My webserver is having some bash issues.  I have Ubuntu 10.04 on a Linode server.  When I ssh just as myself, no sudo su, it just gives me a white $ for the bash prompt.  When I sudo su, it gives me [COLOR="Lime"]root@localhost[/COLOR]:[COLOR="Blue"]/current/directory[/COLOR]# in color.  I have tried editing the ~/.bashrc, I've tried editing the /etc/bash.bashrc, I've tried putting .bashrc in my home directory.  I've tried restarting bash with .~/.bashrc but nothing has worked.  I can do export PS1='whatever' and with the codes (such as \u@\h:\w) it will show just that as the bash prompt (\u@\h:\w).  It does not show the actual [COLOR="Lime"]user@host[/COLOR]:[COLOR="Blue"]/directory[/COLOR].    Also, unless I'm sudo su, I can't hit my up arrow to go back to previously used commands.  This is frustrating me, could anyone help?

---

### Post by AlphaLexman on 2010-07-08
Starting a new instance of bash try:
```
bash --rcfile ~/.yourbashrc
```

[edit] This ony works for interactive shells.

---

### Post by adamcole83 on 2010-07-08
Well that worked at first, but if I exit the ssh session and then ssh back into the server, it goes back to showing just the $

---

### Post by AlphaLexman on 2010-07-08
What are the results of:
```
ssh localhost
```

---

### Post by adamcole83 on 2010-07-08
It just logged me in again and showed $

---

### Post by AlphaLexman on 2010-07-08
Are you sure you are where you think you are and who you are?
```
pwd
```
```
whoami
```

---

### Post by adamcole83 on 2010-07-08
yup, pwd gives my home director and whoami shows my username

---

### Post by AlphaLexman on 2010-07-08
double check your shell:
```
echo $SHELL
```

---

### Post by adamcole83 on 2010-07-08
/bin/sh

---

### Post by AlphaLexman on 2010-07-08
/bin/sh is NOT bash. They are two different shells.

/bin/sh should read a ~/.profile that you could set your prompt in.

---

### Post by adamcole83 on 2010-07-08
This is what my ~/.profile says:


```
# ~/.profile: executed by Bourne-compatible login shells.

if [ "$BASH" ]; then
  if [ -f ~/.bashrc ]; then
    . ~/.bashrc
  fi
fi

mesg n
```

How do I add an else? Would I put it before the first fi or last fi, or should I change it completely to include the ~/.bash in all?

---

### Post by AlphaLexman on 2010-07-08
```
# ~/.profile: executed by Bourne-compatible login shells.

if [ "$BASH" ]; then
  if [ -f ~/.bashrc ]; then
    . ~/.bashrc
  fi
else
PS1=\[\e]0;\u@\h: \w\a\]${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]: \[\033[01;34m\]\w\[\033[00m\] \$
fi

mesg n
```
Just change the PS1=towhateveryouwant-i'mguessingyouknowhow

---

### Post by adamcole83 on 2010-07-08
Eh that didn't work.  I'm over it unless there's a way that it will automatically start bash when I ssh into it.

---

### Post by AlphaLexman on 2010-07-08
Look for any config or *rc files in ~/.ssh

---

### Post by AlphaLexman on 2010-07-08
Try this after you ssh into the server:
```
chsh -s bash
```
should change your login shell to bash.

---

