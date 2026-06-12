---
title: "writing small &quot;suggestive&quot; script"
date: 2010-09-08
forum: General Help
---

### Post by look4 on 2010-09-08
hi ):P

i have learnt how to write scripts that they appears as commands in terminal (put them in bin folder)
what is next, i would like to write a small bash script in a way, that when user enters command and presses tab button, he gets suggestions about possible choices.

i have found out that apache's scripts are put in /etc/rcX.d/something, where X is >= 0, but i guess there should be an organised way to do this?

---

### Post by DaithiF on 2010-09-08
Hi, what you describe is called bash completion.  Take a look at the files in /etc/bash_completion.d to see how this works.  You could copy one of these files and adapt for your purposes.

---

