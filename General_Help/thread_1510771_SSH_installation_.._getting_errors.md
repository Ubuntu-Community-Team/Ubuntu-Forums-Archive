---
title: "SSH installation .. getting errors"
date: 2010-06-16
forum: General Help
---

### Post by paparozoumis on 2010-06-16
It seems like I cannot install ssh
 this is what I get every time
What's wrong with it?
I try ```
sudo apt-get update
``` first and then


```
gigas@Laptop2:~$ sudo apt-get install ssh
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  openssh-server
Suggested packages:
  rssh molly-guard openssh-blacklist openssh-blacklist-extra
The following NEW packages will be installed:
  openssh-server ssh
0 upgraded, 2 newly installed, 0 to remove and 44 not upgraded.
Need to get 0B/286kB of archives.
After this operation, 823kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Selecting previously deselected package openssh-server.
(Reading database ... 233252 files and directories currently installed.)
Unpacking openssh-server (from .../openssh-server_1%3a5.3p1-3ubuntu4_i386.deb) ...
Selecting previously deselected package ssh.
Unpacking ssh (from .../ssh_1%3a5.3p1-3ubuntu4_all.deb) ...
Processing triggers for ureadahead ...
Processing triggers for ufw ...
Processing triggers for man-db ...
Setting up openssh-server (1:5.3p1-3ubuntu4) ...
Creating SSH2 RSA key; this may take some time ...
Creating SSH2 DSA key; this may take some time ...
useradd: cannot lock /etc/passwd; try again later.
adduser: `/usr/sbin/useradd -d /var/run/sshd -g nogroup -s /usr/sbin/nologin -u 116 sshd' returned error code 1. Exiting.
dpkg: error processing openssh-server (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ssh:
 ssh depends on openssh-server; however:
  Package openssh-server is not configured yet.
dpkg: error processing ssh (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 openssh-server
 ssh
E: Sub-process /usr/bin/dpkg returned an error code (1) 
```

---

### Post by sikander3786 on 2010-06-16
> **paparozoumis said:**
> It seems like I cannot install ssh
 this is what I get every time
What's wrong with it?
I try ```
sudo apt-get update
``` first and then


```
gigas@Laptop2:~$ sudo apt-get install ssh
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  openssh-server
Suggested packages:
  rssh molly-guard openssh-blacklist openssh-blacklist-extra
The following NEW packages will be installed:
  openssh-server ssh
0 upgraded, 2 newly installed, 0 to remove and 44 not upgraded.
Need to get 0B/286kB of archives.
After this operation, 823kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Selecting previously deselected package openssh-server.
(Reading database ... 233252 files and directories currently installed.)
Unpacking openssh-server (from .../openssh-server_1%3a5.3p1-3ubuntu4_i386.deb) ...
Selecting previously deselected package ssh.
Unpacking ssh (from .../ssh_1%3a5.3p1-3ubuntu4_all.deb) ...
Processing triggers for ureadahead ...
Processing triggers for ufw ...
Processing triggers for man-db ...
Setting up openssh-server (1:5.3p1-3ubuntu4) ...
Creating SSH2 RSA key; this may take some time ...
Creating SSH2 DSA key; this may take some time ...
useradd: cannot lock /etc/passwd; try again later.
adduser: `/usr/sbin/useradd -d /var/run/sshd -g nogroup -s /usr/sbin/nologin -u 116 sshd' returned error code 1. Exiting.
dpkg: error processing openssh-server (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ssh:
 ssh depends on openssh-server; however:
  Package openssh-server is not configured yet.
dpkg: error processing ssh (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 openssh-server
 ssh
E: Sub-process /usr/bin/dpkg returned an error code (1) 
```

Hi.

Try,

```

sudo apt-get install openssh-server

```

Hope it helps.

Regards.

---

### Post by anglican on 2010-06-16
> **paparozoumis said:**
> It seems like I cannot install ssh
 this is what I get every time
What's wrong with it?
I try ```
sudo apt-get update
``` first and then


```
gigas@Laptop2:~$ sudo apt-get install ssh
Reading package lists... Done
...
useradd: cannot lock /etc/passwd; try again later.
adduser: `/usr/sbin/useradd -d /var/run/sshd -g nogroup -s /usr/sbin/nologin -u 116 sshd' returned error code 1. Exiting.
...

```

That "cannot lock /etc/passwd" looks like the problem. Presumably, some other program is using (and locking) the passwd file. Maybe:
```
lsof /etc/passwd
```Will tell you who/what is doing that.

H

---

### Post by baddnady23 on 2010-06-16
Follow this tutorial.  It works great for me.

[http://principialabs.com/beginning-ssh-on-ubuntu/]("http://principialabs.com/beginning-ssh-on-ubuntu/")

---

### Post by paparozoumis on 2010-06-17
> **sikander3786 said:**
> Hi.

Try,

```

sudo apt-get install openssh-server

```

Hope it helps.

Regards.

I get the same error here, too... 




> **baddnady23 said:**
> Follow this tutorial.  It works great for me.

[http://principialabs.com/beginning-ssh-on-ubuntu/]("http://principialabs.com/beginning-ssh-on-ubuntu/")


It could work if I were able to install the client and the server. 
To start with, I have to 
```
sudo apt-get install openssh-client openssh-server
```
and this is where I get the error messages...



> **anglican said:**
> That "cannot lock /etc/passwd" looks like the problem. Presumably, some other program is using (and locking) the passwd file. Maybe:
```
lsof /etc/passwd
```Will tell you who/what is doing that.

Maybe we are on to something here... 
It looks like this causes the problem

I get that result
```
gigas@Laptop2:~$ lsof /etc/passwd
COMMAND  PID  USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
python  1931 gigas   10r   REG    8,6     1714 2489 /etc/passwd
```

What do I get from that?
Does this help any?

---

### Post by paparozoumis on 2010-06-17
> **paparozoumis said:**
> 
Maybe we are on to something here... 
It looks like this causes the problem

I get that result
```
gigas@Laptop2:~$ lsof /etc/passwd
COMMAND  PID  USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
python  1931 gigas   10r   REG    8,6     1714 2489 s /etc/passwd
```

What do I get from that?
Does this help any?

Finally, with the help of a friend, I found what was causing the problem. 

This command removed the locked file and then the configuration of the package could be completed

```
sudo rm -f /etc/gshadow.lock /etc/shadow.lock /etc/passwd.lock
```

---

