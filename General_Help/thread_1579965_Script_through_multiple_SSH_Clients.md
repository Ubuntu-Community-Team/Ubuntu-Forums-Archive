---
title: "Script through multiple SSH Clients"
date: 2010-09-22
forum: General Help
---

### Post by darukka on 2010-09-22
Hi,

**Short Explaination**
How do I start a script on an ssh server which then starts another script on another ssh server?

**Long Explaination**
I would love to be able to connect to a server with ssh and start a script there which sends a magic packet to my client and waits till it answers the ping. This script is already working, without any problems.
After the client started I would love to be able to ssh into the freshly booted client and start another script that starts a Virtual Machine and waits for the ping to answer. The script is working, but how do I start the second script directly from the first one? Best thing would be if I wouldn't have to put in the ssh password again (as it is the same user and the same password).

---

### Post by BobVila on 2010-09-22
> **darukka said:**
> Hi,

**Short Explaination**
How do I start a script on an ssh server which then starts another script on another ssh server?

**Long Explaination**
I would love to be able to connect to a server with ssh and start a script there which sends a magic packet to my client and waits till it answers the ping. This script is already working, without any problems.
After the client started I would love to be able to ssh into the freshly booted client and start another script that starts a Virtual Machine and waits for the ping to answer. The script is working, but how do I start the second script directly from the first one? Best thing would be if I wouldn't have to put in the ssh password again (as it is the same user and the same password).

What language did you use for the scripts? I do similar things with python (expect and paramiko)

---

### Post by darukka on 2010-09-22
I use Bash

---

