---
title: "LTSP, rc.local and sudo"
date: 2010-05-26
forum: General Help
---

### Post by squaregoldfish on 2010-05-26
I have an LTSP setup, and I want the clients to run some software on startup. I've got a script that runs the software, and I've set up /etc/rc.local to call it at boot time. This works well, but of course the process runs as the root user, which I don't really want. I've wrapped the command with a sudo call as follows:

```
sudo -U steve /usr/local/bin/run.sh
```but I get the following error:

```
sudo: unknown user: steve
```Now, the user steve exists, because I can log in once the LDM appears, but the user's clearly not visible at the time that rc.local is called.

So, how can I get my script to run as the user steve at startup? At what point does the user become available?

TIA,
Steve.

---

### Post by squaregoldfish on 2010-05-30
[LEFT]I'm not generally one for bumping threads, but this one's got me really stumped and it's probably fallen off the radar. I think I've got a workaround up my sleeve, but I'm holding out hope for now...
[/LEFT]

---

