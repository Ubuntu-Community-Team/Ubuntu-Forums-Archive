---
title: "How to permanently alias a command?"
date: 2010-03-06
forum: General Help
---

### Post by Kurtosis on 2010-03-06
My current alias'd commands are:

alias egrep='egrep --color=auto'
alias fgrep='fgrep --color=auto'
alias grep='grep --color=auto'
alias ls='ls --color=auto'

I'd like to change 'ls' and add a few more, is there a command to permanently do that, or a config file I need to edit somewhere?

Thanks!

---

### Post by sisco311 on 2010-03-06
egrep, ... & ls are defined in the ~/.bashrc file. You can define your aliases in ~/.bashrc or ~/.bash_aliases (create it if doesn't exist).

---

### Post by Kurtosis on 2010-03-06
Thanks!

---

