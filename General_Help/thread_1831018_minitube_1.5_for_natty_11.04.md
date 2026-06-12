---
title: "minitube 1.5 for natty 11.04"
date: 2011-08-22
forum: General Help
---

### Post by 2blue on 2011-08-22
I have lubuntu 11.04 (much the same as Ubuntu Natty 11.04), and I am trying to install Minitube. I found a package in package manager, but it turns out to be version 1.3, two versions outdated. I am now trying to upgrade via ppa and terminal, but it turned out to be rather difficult. 

I have followed guidelines I found googling, but neither of them resulted in anything. I get error messages like "command not valid", or I get lost some where in the process when something doesn't run as smoothly as it was hoped. 

Any idea on how to go about this?

---

### Post by kerry_s on 2011-08-22
so your having problems using ppa?

all you need is this part:
```
ppa:ferramroberto/minitube
```

open synaptic package manager
click settings -> repositories
click "other software" tab
click "add"
paste "ppa:ferramroberto/minitube" in to there
click "add source"
close that & click "reload"

you should now have the updated minitube available.

---

### Post by 2blue on 2011-08-23
Thanks Kerry !!!

It worked :P

---

