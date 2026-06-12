---
title: "Virtual box and gaming, plus partitioning"
date: 2010-01-23
forum: General Help
---

### Post by esosa233 on 2010-01-23
HOW SHOULD I PARTITION 362 Gb, and can virtual box on linux handle windows games and mmos. Including maplestory?

---

### Post by earthpigg on 2010-01-23
virtual box isn't very good for 3d games. at all. this is what you should look at: [http://www.winehq.org/](http://www.winehq.org/)

it's in the repos, so you would install it by entering "sudo apt-get install wine" into a terminal.

a perfectly fine partition scheme:
one big partition for /, and 2gb for swap.

a typical partition scheme:
15gb for /
RAM * 1.5 for swap
rest for /home

---

