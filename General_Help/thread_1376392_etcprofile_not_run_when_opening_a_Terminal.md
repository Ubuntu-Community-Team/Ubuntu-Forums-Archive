---
title: "/etc/profile not run when opening a Terminal"
date: 2010-01-09
forum: General Help
---

### Post by thomas_t on 2010-01-09
Every article I read on bash and related shells (e.g. [here]("http://www.thegeekstuff.com/2008/10/execution-sequence-for-bash_profile-bashrc-bash_login-profile-and-bash_logout/")) claim that a bash shell runs /etc/profile first.

However, for me it doesn't, and I wonder why. /etc/bash.bashrc gets run, though. I verify the running of them by having added "echo" commands to both of these scripts.

Here's my setup:
Ubuntu 9.10 (Linux 2.6.31-17-generic on i686), freshly installed, and with all updates applied.
Default shell (bash), which I verified by checking with the "set" cmd, which shows: "SHELL=/bin/bash"

Any idea what could prevent /etc/profile from being run while /etc/bash.bashrc does get run when I open the Terminal app?

Is there some config file that specifies which script gets run by bash? Maybe I need to edit that.

---

### Post by SecretCode on 2010-01-09
Just speculating here: /etc/profile is run by new login shells - go to tty1..6 with ctrl-alt-f1..6 and test it, but is run only once for your X session, not again each time you open a terminal.

Not sure how to force it to be run again for new terminal shells.

---

### Post by thomas_t on 2010-01-09
> **SecretCode said:**
> Just speculating here: /etc/profile is run by new login shell
Seems so. I noticed that when I log in via ssh then profile gets run.

It's just odd because, as a (lame) OSX user I was used to adding global settings through /etc/profile, and now on Ubuntu I have to do it differently. But it makes sense somehow.

---

### Post by QLee on 2010-01-09
[QUOTE=thomas_t]It's just odd because, as a (lame) OSX user I was used to adding global settings through /etc/profile, and now on Ubuntu I have to do it differently. But it makes sense somehow.[/QUOTE]

Should you be looking at bash_profile and bashrc in your users home directory as referenced in the article you cited above?

---

