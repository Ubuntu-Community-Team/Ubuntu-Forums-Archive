---
title: "su command help"
date: 2010-02-28
forum: General Help
---

### Post by cppgraphics on 2010-02-28
Dear folks,

I'm using Ubuntu 9.10 OS, newly installed one. I've only one user which is created by default.

How to know its user rights?

I want to switch to admin mode to execute certain commands, so I gave su command when I enter the admin password it says failure authenticate.

Please help me, 

Thanks in advance.

---

### Post by ajgreeny on 2010-02-28
Ubuntu does not use "su" as most other distros do, it uses sudo instead.  Open a terminal and use "sudo yourcommand" instead, eg ```
sudo apt-get install packagename
```When asked put in your user password, there is no root password in ubuntu, and all will be well.

See [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) for all the details.

---

### Post by Iowan on 2010-02-28
[Here]("https://help.ubuntu.com/community/RootSudo") is a help page that goes into more detail.

---

