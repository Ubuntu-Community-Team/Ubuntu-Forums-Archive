---
title: "The prefix in terminal is too long"
date: 2009-10-28
forum: General Help
---

### Post by oldnumber7 on 2009-10-28
I am using the default terminal. Before I type any commands, the bash prompt looks like:
user@user-desktop:~$

after I type: cd work/example/test/go
the prompt looks like:
user@user-desktop:~/work/example/test/go$

it is way too long and I don't need to show the path detail. How to make it short whenever I enter any directories? like "user@user-desktop:$", or just only a "$"? 
Thanks

---

### Post by The Cog on 2009-10-28
You can change it with a command like:
PS1='Hello there: '

To make it happen every time, put that command in ~/.bashrc

You can enter special sequences like \u for username etc. Use the command **man bash** for details.

---

