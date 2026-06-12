---
title: "Giving back ETC's original Permissions"
date: 2011-07-26
forum: General Help
---

### Post by JzJad on 2011-07-26
Ok, well im kinda new to ubuntu but not totally,
i gave my self full privilege to etc directory kinda on accident
by using "sudo chown -R iaddsign "dir"

so now when i goto run commands like say "sudo apt-get program"
i get back "sudo: /etc/sudoers is owned by uid 1000, should be 0
segmentation fault"
 so i need to give back original permissions :) help please and ty

---

### Post by Wayne_V on 2011-07-26
try just "chown root:root /etc/sudoers"   that should work if you are currently user iaddsign

then you can at least use sudo again.

---

### Post by JzJad on 2011-07-26
> **Wayne_V said:**
> try just "chown root:root /etc/sudoers"   that should work if you are currently user iaddsign

then you can at least use sudo again.
Nope, i got this,
"chown: changing ownership of '/etc/sudoers': operation not permitted'

:(

---

### Post by Wayne_V on 2011-07-26
do ls -l /etc/sudoers and check --- it may have worked even with that error.

never mind -- probably not.  You'll have to boot recovery mode to do it.

---

### Post by JzJad on 2011-07-26
is command not found
----------------------
didnt work i also tried apt get and same error
---
second thought im just going to start over because i just realized i haver ver. 9,10 and need to update it

---

### Post by Wayne_V on 2011-07-26
that's ell-ess, not eye-ess.  

But updating via CD should work just fine as well.

---

### Post by JzJad on 2011-07-26
ok ya i used both commands XD but thanks for the help :) its appreciated

---

