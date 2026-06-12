---
title: "Warning: Fake initctl called, doing nothing."
date: 2011-05-10
forum: General Help
---

### Post by Angellus_Mortis on 2011-05-10
I do not know why, but I have tried to install both MySQL and SSH. Everytime I do thry install, but I always get the error: 

"Warning: Fake initctl called, doing nothing."

It also does that whenever I try to stop or start the services.

Here is a terminal piece


```

chris@Jesse-Compaq:~$ sudo apt-get install ssh
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  user-setup localechooser-data
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  openssh-client openssh-server
Suggested packages:
  ssh-askpass libpam-ssh keychain openssh-blacklist openssh-blacklist-extra
  rssh molly-guard
The following NEW packages will be installed:
  openssh-client openssh-server ssh
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 866 kB/1,177 kB of archives.
After this operation, 3,166 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ natty/main openssh-client i386 1:5.8p1-1ubuntu3 [865 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ natty/main ssh all 1:5.8p1-1ubuntu3 [1,280 B]
Fetched 866 kB in 2s (409 kB/s) 
Preconfiguring packages ...
Selecting previously deselected package openssh-client.
(Reading database ... 155856 files and directories currently installed.)
Unpacking openssh-client (from .../openssh-client_1%3a5.8p1-1ubuntu3_i386.deb) ...
Selecting previously deselected package openssh-server.
Unpacking openssh-server (from .../openssh-server_1%3a5.8p1-1ubuntu3_i386.deb) ...
Selecting previously deselected package ssh.
Unpacking ssh (from .../ssh_1%3a5.8p1-1ubuntu3_all.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Processing triggers for ufw ...
Setting up openssh-client (1:5.8p1-1ubuntu3) ...
Setting up openssh-server (1:5.8p1-1ubuntu3) ...

Warning: Fake initctl called, doing nothing.
Setting up ssh (1:5.8p1-1ubuntu3) ...
chris@Jesse-Compaq:~$ ssh localhost
ssh: connect to host localhost port 22: Connection refused
chris@Jesse-Compaq:~$ 

```

---

### Post by Angellus_Mortis on 2011-05-11
Bump. I cannot finish working on my server until I figure this out :( I have never had this issue before.

---

### Post by echs on 2011-08-05
i've run into similar problems on my desktop natty 64bit installation.

first i tried running ssh directly to see whats going on and i got an error:
```

$ sudo /usr/sbin/sshd -D
Missing privilege separation directory: /var/run/sshd

```

i looked for that dir and it was missing, so i created it (like the init script in /etc/init/ssh.conf should do..):
```

$ sudo mkdir -p -m0755 /var/run/sshd

```

now i could run the ssh daemon standalone, but running the init script via **sudo start ssh** still gives me an error:

**Warning: Fake initctl called, doing nothing.**

i just don't know anything else to do :confused:

hope this helps! [-o<

---

### Post by danielmncastro on 2013-03-26
This is an old thread, but I just had the same problem and thought I should post here for future references. 

In my case, what happened was some problem during the installation so something was not quite right. Reinstalling upstart worked:

```
sudo apt-get install upstart --reinstall
```

Good luck, folks.

---

### Post by oldos2er on 2013-03-26
Old thread closed.

---

