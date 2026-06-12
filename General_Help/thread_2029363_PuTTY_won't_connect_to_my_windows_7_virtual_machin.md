---
title: "PuTTY won't connect to my windows 7 virtual machine"
date: 2012-07-19
forum: General Help
---

### Post by fishsticks1907 on 2012-07-19
Using Ubuntu 12.04, and they can ping to each other, but ssh or putty wont connect to windows. any help would be great.

---

### Post by papibe on 2012-07-19
Hi fishsticks1907.

What kind ssh service are you running on Windows?

Could you post a log of an ssh attempt using the triple verbose options. For instance:
```
ssh -v user@machine
```
Regards.

---

### Post by fishsticks1907 on 2012-07-20
> **papibe said:**
> Hi fishsticks1907.

What kind ssh service are you running on Windows?

Could you post a log of an ssh attempt using the triple verbose options. For instance:
```
ssh -v user@machine
```Regards.

This is what i get:

marcio@Ubuntu-PC:~$ ssh -v windows@windows-PC
OpenSSH_5.9p1 Debian-5ubuntu1, OpenSSL 1.0.1 14 Mar 2012
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug1: Connecting to windows-PC [192.168.1.41] port 22.
debug1: connect to address 192.168.1.41 port 22: Connection timed out
ssh: connect to host windows-PC port 22: Connection timed out

---

### Post by papibe on 2012-07-20
Thanks.

It looks like there's no service running, or it is being blocked by the Windows firewall. Disable your firewall to make tests.

Again, What kind ssh service are you running on Windows?

Regards.

---

### Post by fishsticks1907 on 2012-07-20
> **papibe said:**
> Thanks.

It looks like there's no service running, or it is being blocked by the Windows firewall. Disable your firewall to make tests.

Again, What kind ssh service are you running on Windows?

Regards.

no idea, nothing i guess. i thought i didn't need anything on the windows 7 machine? just the ssh or putty on ubuntu.

---

### Post by papibe on 2012-07-20
I'm afraid that's not going to work.

Windows doesn't provide ssh services by itself. You would need to install a software that receive the connections. Unfortunately, I can't recommend you something because I'm not familiar with that.

Windows provides a remote desktop option, but only for the higher versions (professional and ultimate I think).

Regards.

EDIT: Now that I think about it, I know about Cygwin, but I don't know details.

---

### Post by Whovian on 2012-07-20
Putty will not work in ubuntu because it is meant for windows only an is a ssh client.  also check an see if port 22 is open in the windows firewall cause like papibe said it might be blocking it.

---

