---
title: "Slow SSH"
date: 2011-02-05
forum: General Help
---

### Post by wjp on 2011-02-05
Hi,

Since upgrading to the latest ubuntu 10.10 my SSH has been slow to connect.
Here's the trace:

debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *

Pauses here for 7 seconds.

debug1: Connecting to  [91.194.74.15] port 22.
debug1: Connection established.
debug1: identity file /home/wayne/.ssh/id_rsa type -1
debug1: identity file /home/wayne/.ssh/id_rsa-cert type -1
debug1: identity file /home/wayne/.ssh/id_dsa type -1
debug1: identity file /home/wayne/.ssh/id_dsa-cert type -1
debug1: Remote protocol version 2.0, remote software version Sun_SSH_1.1.1
.... after this point is fast and prompts for the password


Has anyone got any ideas here? If I cannot using putty from the windows partition is almost instant.

thanks
Wayne

---

### Post by wjp on 2011-02-05
hmmm seems to be something with the DNS lookup, as when I use the straight IP address it's quick.

Any ideas?

---

