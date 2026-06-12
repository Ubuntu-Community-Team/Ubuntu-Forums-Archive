---
title: "SSH login with X11 forwarding running host commands"
date: 2010-08-12
forum: General Help
---

### Post by ordealbyfire83 on 2010-08-12
When logging into a remote computer using ssh -Y (or ssh -X), sometimes applications on the HOST system are launched instead. Improper, I suppose? I'm running 10.04, fully updated as of today. As an example, if I log in like so, ssh -Y username@remotelocation and then try to launch a program such as /usr/bin/firefox, the firefox on the host will launch. However, if I try launching a program not available on the host, then the remote application is used.

I would expect that once logged into a remote computer, all commands entered via the terminal go there. Is this behavior expected, and if so, is it possible to work around it?

---

