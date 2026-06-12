---
title: "bash_history HISTCONTROL help"
date: 2010-12-02
forum: General Help
---

### Post by COKEDUDE on 2010-12-02
Can anyone tell me why this is not working? 

```
export HISTCONTROL=ignoreboth
```

---

### Post by efflandt on 2010-12-02
Describe "not working".  If you type the same command repeatedly one after, another is that command replicated multiple times in your .bash_history?  If you begin a command line with a space, does that command come up when you hit up cursor after that.

That actually seems to be a default for me in maverick bash, even though I have not specifically set HISTCONTROL.

---

### Post by AlphaLexman on 2010-12-02
Where are you invoking this variable?

in '~/.bashrc' ?

Is it being overwritten somewhere else?

Could you post a snippet output of
```
history
```
that shows duplicates or spaces?

---

### Post by COKEDUDE on 2010-12-02
> **AlphaLexman said:**
> Where are you invoking this variable?

in '~/.bashrc' ?

Is it being overwritten somewhere else?

Could you post a snippet output of
```
history
```
that shows duplicates or spaces?

Is that enough or want more? The spaces in the front are being ignored but the duplicates are not being ignored. 

```
exit
ls
ls
ls
history
vi .bash_history
export HISTCONTROL=ignoreboth
ls
ls
ls
vi .bash_history
exit

```

---

### Post by AlphaLexman on 2010-12-02
> **AlphaLexman said:**
> Where are you invoking this variable?

in '~/.bashrc' ?

```
cat /etc/profile
cat ~/.profile
cat ~/.bash_login
cat ~/.bash_profile
cat ~/.bashrc

```
You don't have to post each one... but which one(s) have set the variable:
> export HISTCONTROL=ignoreboth

Note: The further DOWN the list will override those above!

---

