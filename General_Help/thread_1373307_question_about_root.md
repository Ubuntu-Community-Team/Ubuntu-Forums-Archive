---
title: "question about root"
date: 2010-01-05
forum: General Help
---

### Post by Peter Crncec on 2010-01-05
Hi

I started to use Ubuntu 9.1 today. It's the first version of linux i'm using.

So my problem is that i always got a message in terminal, that says "are you root?", when i try to do something with apt-get.
Well i tried to install a root, but it didn't work. What should i do to fix this problem?
:confused:

Oh one thing i almost forgot. Root is the Superuser that should be put on, when i installed the current version of ubuntu right? I don't understand how could it happen that the system didn't put the root on,
i would be happy if someone tells me something :P

---

### Post by doas777 on 2010-01-05
just FYI, ubuntu does not use a root account like other distros.
here is some info about how to run a command or application with root privledges:
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

it comes down to adding 'sudo' or 'gksu' to the beginning of commands. they will prompt for a password, but it is the password of the logged in user that they are requesting, not a root password. sudo is for command line apps, gksu is for graphical ones.

---

### Post by Peter Crncec on 2010-01-05
ah great =) i wondered why there was used "sudo" thanks.

---

