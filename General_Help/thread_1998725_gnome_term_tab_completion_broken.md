---
title: "gnome term tab completion broken"
date: 2012-06-07
forum: General Help
---

### Post by bobdobbs on 2012-06-07
I'm using a fresh installation of 12.04. 

I'm using gnome-term under KDE. But I get the same problem with konsole as well.

In my bash profile, I define and export variables, to make navigation easier. For example, I have '$HOSTS'. This is a shortcut to the directory under which I have a number of apache virtual hosts.

In a normal installation of linux, I can do 'ls $HOSTS/', then hit tab, and get a listing of that directory.

However, in ubuntu 12.04, when I hit tab, a backslash appears in front of the '$', and the string becomes useless.

In other words, I get this

'ls \$HOSTS'

What is going on here? How do I get the normal behaviour back?

---

### Post by bobdobbs on 2012-06-08
bump

---

### Post by Vaphell on 2012-06-08
[http://ss64.com/bash/shopt.html](http://ss64.com/bash/shopt.html)

set cdable_vars

edit: what i mentioned would suggest variable names when you press tab with $ typed in
behavior described is introduced in bash 4.2 and is a bug
[http://askubuntu.com/questions/41891/bash-auto-complete-for-environment-variables](http://askubuntu.com/questions/41891/bash-auto-complete-for-environment-variables)

check if your bash supports direxpand option which should bring the old behavior back

---

### Post by bobdobbs on 2012-06-09
> **Vaphell said:**
> [http://ss64.com/bash/shopt.html](http://ss64.com/bash/shopt.html)


check if your bash supports direxpand option which should bring the old behavior back

How can I check this ?

---

### Post by codemaniac on 2012-06-09
In your ~/.bashrc file , have you checked if the below lines are uncommented .Go to line no 98 .
```

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if [ -f /etc/bash_completion ] && ! shopt -oq posix; then
    . /etc/bash_completion
fi
```

---

### Post by bobdobbs on 2012-06-09
That block of code is indeed in my profile, and is uncommented.

---

### Post by codemaniac on 2012-06-09
As superuser try edit the file /etc/bash.bashrc and uncomment the following lines .

```

# enable bash completion in interactive shells
#if [ -f /etc/bash_completion ] && ! shopt -oq posix; then
#    . /etc/bash_completion
#fi
```

PS: Always take a back up of the original file before any changes made .

```
cp /etc/bash.bashrc /etc/bash.bashrc.orig
```

---

### Post by bobdobbs on 2012-06-09
Ok...

I backed up /etc/bash.bashrc, then edited the working version as per your instructions.

Then I opened a new terminal as a normal user.

TAB still injects the prefix.

Thanks for the help, but I'm going to give up on this and surrender to using zsh for the time being. I've used zsh before. It's similar enough to provide a good working environment.

---

### Post by codemaniac on 2012-06-09
try sourcing the mentioned script in the current terminal .
```
. /etc/bash.bashrc
```

---

### Post by bobdobbs on 2012-06-09
> **codemaniac said:**
> try sourcing the mentioned script in the current terminal .
```
. /etc/bash.bashrc
```

I'm afraid that that didn't work.

I also ran this test from a normal users shell:

. /etc/bash_completion

And the abberant behaviour persists.

---

### Post by Vaphell on 2012-06-09
**shopt -p** prints settings and their status
unfortunately the direxpand option is not available in bash present in precise (just checked in , if it was it would require **shopt -s direxpand**

---

