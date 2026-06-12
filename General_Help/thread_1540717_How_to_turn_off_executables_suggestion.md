---
title: "How to turn off executables suggestion"
date: 2010-07-28
forum: General Help
---

### Post by aneganov on 2010-07-28
Hi,

when I mistype a name of an executable program in terminal, ubuntu tries to search for similar programs in packages and then suggests names. This takes time, slowing down work and entirely useless for me. How to turn this feature off?

thanks

p.s. I personally can't even find a reason for implementing this feature and rather making it turned on by default. If someone needs a tool, he/she can search through packages.

---

### Post by anglican on 2010-07-28
> **aneganov said:**
> Hi,

when I mistype a name of an executable program in terminal, ubuntu tries to search for similar programs in packages and then suggests names. This takes time, slowing down work and entirely useless for me. How to turn this feature off?

thanks

p.s. I personally can't even find a reason for implementing this feature and rather making it turned on by default. If someone needs a tool, he/she can search through packages.
The command-not-found stuff is set up in /etc/bash.bashrc (it's at the end of that file). Just remove, or comment out those lines and it's gone.

H

---

### Post by aneganov on 2010-07-28
Thank you for reply, anglican!
Would you be more specific? We are not talking about bash completion, right? I mean, when you type something and press Return and if command not found, then something suggests packages, where this command may be found.

UPD. ops, sorry. You WERE enough specific actually :) I found that stuff, thank you!

---

