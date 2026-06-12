---
title: "unable to ssh or scp into my own system from server"
date: 2010-10-23
forum: General Help
---

### Post by jsriz on 2010-10-23
I am able to ssh into my server from my laptop but unable to scp my files to my laptop it just gives me:
```
ssh: connect to host 192.xxx.xxx.xxx port 22: Connection timed out
lost connection

```
again 
upon trying to ssh into my laptop from there gives me the same result.
please help......

---

### Post by luvshines on 2010-10-23
When you try to ssh to your laptop, try adding -vv with ssh command to see the verbose which can give some hint where it hangs

Also make sure that no firewall is blocking the transfers

---

### Post by mikewhatever on 2010-10-23
Is the openssh-server package installed on the laptop? By default, only the client is installed and not the server, so that you should be able to ssh from, but not to the default installation.

---

### Post by jsriz on 2010-10-24
> **mikewhatever said:**
> Is the openssh-server package installed on the laptop? By default, only the client is installed and not the server, so that you should be able to ssh from, but not to the default installation.
yes i had already installed that and am able to scp from other browsers except for this one in particular
herZ the result of th scp with -vv option
```
Executing: program /usr/bin/ssh host 192.168.74.250, user xxx, command scp -v -t .
OpenSSH_5.3p1 Debian-3ubuntu4, OpenSSL 0.9.8k 25 Mar 2009
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 192.168.74.250 [192.168.74.250] port 22.
debug1: connect to address 192.168.74.250 port 22: Connection timed out
ssh: connect to host 192.168.74.250 port 22: Connection timed out
lost connection
```

---

### Post by efflandt on 2010-10-24
What do you mean by "**able to scp from other browsers except for this one**", do you mean from other computers?  If you have .ssh directory in home dir (~/.ssh) of either computer, what are its permissions?  Your ~/.ssh should have 700 permissions drwx------ and any files in it should have 600 permissions -rw-------.

And check /var/log/messages of the computer you are trying to ssh to, to see if there is mention of anything there.

---

### Post by luvshines on 2010-10-24
> **jsriz said:**
> yes i had already installed that and am able to scp from other browsers except for this one in particular
herZ the result of th scp with -vv option
```
Executing: program /usr/bin/ssh host 192.168.74.250, user xxx, command scp -v -t .
OpenSSH_5.3p1 Debian-3ubuntu4, OpenSSL 0.9.8k 25 Mar 2009
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 192.168.74.250 [192.168.74.250] port 22.
debug1: connect to address 192.168.74.250 port 22: Connection timed out
ssh: connect to host 192.168.74.250 port 22: Connection timed out
lost connection
```

Did you also check the firewall on your laptop ??

From the other machine, also check the connectivity to your laptop's port 22
```
nc -zv <laptop-ip> 22
```

---

