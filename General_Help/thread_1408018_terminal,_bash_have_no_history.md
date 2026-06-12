---
title: "terminal, bash have no history"
date: 2010-02-15
forum: General Help
---

### Post by manosx on 2010-02-15
For every new terminal i open i have no history; the history is kept only in that terminal and is gone when i exit the terminal.
If I count lines:
as a user:
```

$ wc -l .bash_history
wc: .bash_history: Permission denied

```
but when sudo there are 500 lines:
```

$ sudo wc -l .bash_history
500 .bash_history

``` 
so there is history.. how can I have the history in my bash??
Is the history/permission like this in your computers?

---

### Post by Richard1979 on 2010-02-15
Maybe try this:

```
sudo chown YOU:YOU /home/YOU/.bash_history
```Replace YOU with your username.

---

### Post by manosx on 2010-02-15
i couldn't do it as user but it worked with sudo

Ah and what I was doing before it stopped working?:
```

cat /dev/urandom| tr -dc 'a-zA-Z0-9-_!@#$%^&*()_+{}|:<>?='|fold -w 40| head -n 4| grep -i '[!@#$%^&*()_+{}|:<>?=]'

```
I was making passwords or smth :D

it works well now
thank you!

---

