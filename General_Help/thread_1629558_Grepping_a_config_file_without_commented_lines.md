---
title: "Grepping a config file without commented lines"
date: 2010-11-23
forum: General Help
---

### Post by byb3 on 2010-11-23
Hi All,

What command would you suggest to be able to grep a config file but to only display the active portion of the file?

Take my terrible example below:

[B]### useless comment
### inactive comment
ip address 1.1.1.1 # < - ip address

# do this
# do this as well
netmask 255.255.255.0[/B]

I would like the output to be:
ip address 1.1.1.1
netmask 255.255.255.0

Cheers!

---

### Post by SeijiSensei on 2010-11-23
grep -v '^#' file

That displays only lines not (-v) starting (^) with a hash mark in "file".

---

### Post by lmarmisa on 2010-11-23
This command will filter lines starting with char #:

```

grep -v ^# file

```

---

