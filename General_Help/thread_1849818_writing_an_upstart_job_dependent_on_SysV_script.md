---
title: "writing an upstart job dependent on SysV script"
date: 2011-09-25
forum: General Help
---

### Post by spleach on 2011-09-25
Hi,
I have written an upstart configuration file for a job that depends on bind9 running. Bind9 doesn't have an upstart job, nor does it emit an init event, so I can't figure out the correct `start on` stanza which I need.

One possibility is to add a 'sleep X' line to the pre-start or script stanzas, but that seems a dirty hack.

How else though can I make this upstart job start only after bind9? Another option is to add a line to the /etc/init.d/bind9 file:-
```
initctl emit bind9
```However, modifying bind9's init.d script isn't very portable, and would be a hack outside of the responsibility of my program.

Any suggestions??

TIA,
Alex

EDIT: Things I've tried:-
```
start on (net-device-up and started smbd)   # starts too early.
start on started rc  # still too early.
start on runlevel [2] # again, still too early...
start on (started bind9 or started named) # neither of these events exist according to `initctl list`

```

---

