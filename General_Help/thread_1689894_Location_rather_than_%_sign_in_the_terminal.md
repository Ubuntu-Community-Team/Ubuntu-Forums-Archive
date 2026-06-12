---
title: "Location rather than % sign in the terminal"
date: 2011-02-17
forum: General Help
---

### Post by James_Lochhead on 2011-02-17
Hi everyone,

I have been recently been using Ubuntu machines in my faculty labs at university that have % as the terminal sign for the line rather than the location.

For example,

% kate &
% echo "helloooo" > hello.txt
%

I find this extremely annoying as I am used to % being replaced with a path to the current directory followed by a $. Like a default Ubuntu install.

For example,

james@james-pc:~$ cd Documents
james@james-pc:~/Documents$

I would like to know if there is an easy way to change this to what I am used to? I don't necessarily need the "james-pc" bit, the username would be nice but I really want the path to the directory.

---

### Post by TeoBigusGeekus on 2011-02-17
Download [this]("http://sourceforge.net/projects/linuxcommand/files/TLCL/09.12/TLCL-09.12.pdf/download") book and look at chapter 14: Customizing the prompt.

---

### Post by Habitual on 2011-02-18
C:\home\jj\>

with this addition to your .bashrc
```
DOS='C:${PWD//\//\\\}>'
PS1="\[\033[00m\]\[\033[01;31m\]$MKF\n\[\033[00m\]\[\033[01;39m\]$DOS\[\033[00m\]"
```

You really can make the prompt do almost anything.

---

