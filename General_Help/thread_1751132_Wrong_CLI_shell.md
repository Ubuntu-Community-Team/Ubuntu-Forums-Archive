---
title: "Wrong CLI shell"
date: 2011-05-06
forum: General Help
---

### Post by megabuffen on 2011-05-06
When i connect to my server with the user account created during installation, I get a normal bash shell. It works the same way if I su to root. However, if I create a new user with useradd, that user will just see a $ at the start of the line if they log in over ssh or if I su to that user. Also, TAB autocomplete won't work, and the same applies to a number of shell commands.

How do I fix this?

---

### Post by Lars Noodén on 2011-05-06
You can reset the default shell for that user with **usermod**
```

usermod --shell /bin/bash *user*

```

Or you could type **bash** each time.

---

### Post by KeyserSoze93 on 2011-05-06
Try using adduser rather than useradd. It may be that useradd doesn't set the proper default shell which you would get with adduser.

---

### Post by megabuffen on 2011-05-06
I tried usermod -s /bin/bash *user* and I am now getting the correct shell. However, it is still lacking some commands, such as the ls -la shortcut ll. Why is there a difference between user accounts?

---

### Post by Lars Noodén on 2011-05-07
**adduser** will set a lot of defaults, **useradd** just gives bare bones.   Which did you use to create the account?

---

### Post by matt_symes on 2011-05-07
Hi

> ls -la shortcut ll is an alias set up in a users .bashrc file, the hidden file in the users home directory.

```

matthew@matthew-laptop:~$ grep "alias" .bashrc
# enable color support of ls and also add handy aliases
    alias ls='ls --color=auto'
    #alias dir='dir --color=auto'
    #alias vdir='vdir --color=auto'
    alias grep='grep --color=auto'
    alias fgrep='fgrep --color=auto'
    alias egrep='egrep --color=auto'
# some more ls aliases
alias ll='ls -alF'
alias la='ls -A'
alias l='ls -CF'
# ~/.bash_aliases, instead of adding them here directly.
if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
matthew@matthew-laptop:~$ 
```

As has been pointed out, these are not created with the useradd command. Try to use adduser command and you will get all the defaults.

BTW:  

> that user will just see a $ at the start of the line

That, i believe, is the DASH shell.

Kind regards

---

### Post by nothingspecial on 2011-05-07
Hi,

You probably need to copy /etc/skel/.bashrc to each users $HOME

```
su <newuser>
cd
cp /etc/skel/.bashrc .
```

---

### Post by Lars Noodén on 2011-05-07
Alternately, if there is nothing you need to save, then you  can delete the user and re-create it with **adduser** to get the right defaults.

---

