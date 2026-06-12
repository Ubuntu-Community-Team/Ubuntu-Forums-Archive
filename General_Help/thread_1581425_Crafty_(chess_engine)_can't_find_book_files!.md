---
title: "Crafty (chess engine) can't find book files!"
date: 2010-09-24
forum: General Help
---

### Post by bugsduggan on 2010-09-24
Hi I'm using Ubuntu 10.04 LTS and I've installed Crafty from the synaptec package manager. All good so far. I type ```
crafty
```
and then I get:
```

unable to open book file [./book.bin].
book is disabled
unable to open book file [./books.bin].

Crafty v23.1 (1 cpus)

White(1): quit

```

I did manage to find one post on another forum alluding to the same problem [here]("https://bugs.launchpad.net/ubuntu/+source/crafty/+bug/533756"), but I (being a bit new to all this command line stuff) can't make head nor tail of it.

Any help would be greatly appreciated.

---

### Post by bugsduggan on 2010-09-24
Managed to solve my own problem!

Crafty's default install is a bit wonky when it comes to putting the books in a sensible place. You will need to:

```
cd /usr/share/doc/crafty
sudo chmod +x setup_crafty.sh
./setup_crafty.sh
```

Don't run the last command as root! It will spit out a few lines of info and then ask you to

```
source /home/<USERNAME>/.crafty/env_settings
```

Then when you run crafty you get:

```
hash table memory =    8M bytes.
pawn hash table memory =    2M bytes.
show book statistics
EGTB access enabled
using tbpath=/home/bugs/.crafty
0 piece tablebase files found
parallel threads disabled.


Crafty v23.1 (1 cpus)

White(1): 
```

---

