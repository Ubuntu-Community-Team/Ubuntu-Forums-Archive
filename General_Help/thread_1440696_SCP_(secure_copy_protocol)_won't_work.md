---
title: "SCP (secure copy protocol) won't work"
date: 2010-03-27
forum: General Help
---

### Post by marre4444 on 2010-03-27
When executing the next command: scp -v /home/marnik/new Marnik@192.168.1.5:

I seem to be unable to connect to my windows client. What may be causing this problem?
I am writing a program in C#.net and make use of the sharpSSH library, since it didn't seem to work I tried out the scp command on de server itself. Below you find the debug info



marnik@spirit:/$ scp -v /home/marnik/new Marnik@192.168.1.5:
Executing: program /usr/bin/ssh host 192.168.1.5, user Marnik, command scp -v -t .
OpenSSH_4.7p1 Debian-8ubuntu1.2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to 192.168.1.5 [192.168.1.5] port 22.


Kind regards



EDIT:  problem has been solved  =>  solution
Add a rule in the windows firewall to allow incomming connections on port 22.

---

