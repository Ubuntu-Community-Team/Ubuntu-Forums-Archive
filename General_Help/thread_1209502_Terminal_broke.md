---
title: "Terminal broke"
date: 2009-07-10
forum: General Help
---

### Post by xandrex on 2009-07-10
Hello,

so i'm new, SURPRISE!  anyways, this is what happened: I ran a dpkg slapd_2.4.15-1ubuntu3_amd64.deb and it failed because of missing dependencies. Ok, not a big deal right? wrong!  nwo my terminal is wacked.  I can't see what I'm typing and when I hit neter the prompt doesn't go down to the next line, it just comes up on the side.

mendea1@ubuntu:~$ mendea1@ubuntu:~$ mendea1@ubuntu:~$

thank you,

Andre

---

### Post by t4thfavor on 2009-07-10
Did you reboot? it usually helps clear up screwy terminals.

---

### Post by xandrex on 2009-07-10
yep, twice. still nothing though :(.

---

### Post by agathian on 2009-07-14
xandrex,

I am not sure if the failed package installation and terminal mess up are related - but one never knows.

Typically terminal settings are handled via the command "stty".

I would suggest trying this in the terminal to see if it helps
```
stty sane
```

If the reboot is not clearing things up, then either the user settings or global settings is messed up. are there any other user in the system you can test?

---

