---
title: "Two questions about Upstart scripts"
date: 2011-02-04
forum: General Help
---

### Post by minaev on 2011-02-04
I'm trying to write Upstart scripts for a program that I'd like to restart automatically, but cannot even start/stop it properly.

1. `pid file' won't work because there is no such file for the program. `pid binary' won't work either, because there can be more than one instance of the binary (which is, basically, a Erlang virtual machine) running. Are there other ways to pass PID to Upstart? I can get PID from a script.

2. Is there a way to define a proper shutdown command for the service?

Thank you.

---

