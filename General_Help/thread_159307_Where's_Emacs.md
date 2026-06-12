---
title: "Where's Emacs?"
date: 2006-04-12
forum: General Help
---

### Post by Cullen Schaffer on 2006-04-12
I'm a new Ubuntu user, but generally familiar with Unix.  I installed
Ubuntu, opened a terminal window and was surprised to find that
emacs was unrecognized.  Ditto for gcc.  Do I need to do something
to get access to these and other basic programs?

---

### Post by psychicdragon on 2006-04-12
They're not installed by default in Ubuntu. You can get them by typing this into the terminal:
```
sudo apt-get install emacs build-essential
```

---

### Post by Cullen Schaffer on 2006-04-14
I followed this advice, but when I tried

  sudo apt-get install emacs build-essential

I got the error message

E: couldn't find package emacs

I had gotten the same error earlier in trying

  sudo apt-get install emacs21

Any thoughts?

---

### Post by krismatth3 on 2006-04-14
Enable the universe repository in /etc/apt/sources.list and then 'sudo apt-get install emacs21'

---

### Post by PriceChild on 2006-04-14
don't forget to

```
sudo apt-get update
```

first

---

### Post by krismatth3 on 2006-04-14
Whoops. *blush*

---

### Post by Cullen Schaffer on 2006-04-15
[QUOTE=krism]Enable the universe repository in /etc/apt/sources.list and then 'sudo apt-get install emacs21'[/QUOTE]

What does it mean to *enable* the universe repository?  Do I need Internet access to do it?

---

