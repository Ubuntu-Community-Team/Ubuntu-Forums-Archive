---
title: "arch linux install programs"
date: 2010-04-23
forum: General Help
---

### Post by sxmaxchine on 2010-04-23
How can i install programs using archbang. I have been trying to install geany i have downloaded the source and i have cd to the directory with no problems then i run ./configure with no problems however when i try to run the 'make' command i get told that the command does not exist.

what am i doing wrong this is my first time to use arch.

and im sorry to ask an arch question on the ubuntu forums.

---

### Post by Simian Man on 2010-04-23
Why not install geany with pacman?

```

pacman -S geany

```

---

### Post by sxmaxchine on 2010-04-23
> **Simian Man said:**
> Why not install geany with pacman?

```

pacman -S geany

```

thanks for the reply but when i try that i get this error message
error: 'geany': not found in sync db

---

### Post by sxmaxchine on 2010-04-23
> **sxmaxchine said:**
> thanks for the reply but when i try that i get this error message
error: 'geany': not found in sync db

i also tried it for vlc and pidgin

---

### Post by snowpine on 2010-04-23
You are in way over your head. :) Take a deep breath, make a cup of coffee, and read this: [http://wiki.archlinux.org/index.php/Beginners%27_Guide](http://wiki.archlinux.org/index.php/Beginners%27_Guide)

---

### Post by sxmaxchine on 2010-04-24
i think i have solved my problem but now i have another problem.
i try to create my repositories by running:

sudo pacman -Syy

however when i do this i get this error

$ sudo pacman -Syy
Password: 
:: Synchronizing package databases...
error: failed to update core (no servers configured for repository)
error: failed to update extra (no servers configured for repository)
error: failed to update community (no servers configured for repository)
error: failed to synchronize any databases

---

### Post by snowpine on 2010-04-24
What does your /etc/pacman.d/mirrorlist look like?

---

### Post by sxmaxchine on 2010-04-25
Hello thanks for the response and the problem with the mirrorlist was that it was uncommented. sorry i forgot to mention the problem was solved. Thank you for the help.

---

