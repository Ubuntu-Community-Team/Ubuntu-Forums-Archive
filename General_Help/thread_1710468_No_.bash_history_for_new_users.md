---
title: "No .bash_history for new users?"
date: 2011-03-19
forum: General Help
---

### Post by Thund3rstruck on 2011-03-19
Hi guys. I created some new accounts on a dev seat:
```

useradd -m newUser1

```

Users get created fine and can log in but are missing all the bash files (.bashrc, .bash_history, etc). When these users try to use the up and down arrows to view shell history they get junk characters. I checked and there is no history file in their homes. 

```

$ echo $HISTFILE

```

returns nothing. Where is the environmental variable set and how can I get this working?

/Linux Mint 9 (which is based on Ubuntu 10.04)

Thanks!

---

### Post by Thund3rstruck on 2011-03-19
Nevermind... I figured it out.

New accounts are configured to use the /bin/sh shell and not /bin/bash. Edited the /etc/passwd file to specify /bin/bash and we're good to go!

---

