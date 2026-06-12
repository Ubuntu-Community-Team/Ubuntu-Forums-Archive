---
title: "Frozen/old welcome message"
date: 2011-06-07
forum: General Help
---

### Post by oliverweidel on 2011-06-07
Hello,

I've a problem with the welcome message. As you can see the welcome message with landscape-sysinfo is written twice. The second welcome message is the older one which is something like frozen:

```
login as: oliver
oliver@xx.de's password:
Linux xx 2.6.32-32-server #62-Ubuntu SMP Wed Apr 20 22:07:43 UTC 2011 x86_64 GNU/Linux
Ubuntu 10.04.2 LTS

Welcome to the Ubuntu Server!
 * Documentation:  http://www.ubuntu.com/server/doc

  System information as of Wed Jun  8 01:40:26 CEST 2011

  System load:    0.0              Processes:           114
  Usage of /home: 41.0% of 941MB   Users logged in:     0
  Memory usage:   50%              IP address for eth1: xx
  Swap usage:     0%

  Graph this data and manage this system at https://landscape.canonical.com/

Ubuntu 10.04.2 LTS

Welcome to the Ubuntu Server!
 * Documentation:  http://www.ubuntu.com/server/doc

  System information as of Wed May 18 23:15:17 CEST 2011

  System load:    0.25             Processes:           122
  Usage of /home: 41.0% of 941MB   Users logged in:     1
  Memory usage:   25%              IP address for eth1: xx
  Swap usage:     1%

  Graph this data and manage this system at https://landscape.canonical.com/

35 packages can be updated.
0 updates are security updates.

Last login: Wed Jun  8 01:30:28 2011 from xx.de
oliver@studi:~$

```Any idea how to resolve this issue?

Thank you very much in advance!

Regards, Oliver

---

### Post by AlphaLexman on 2011-06-07
Look in these files for clues:
[LIST]
[*]/etc/profile
[*]~/.bash_profile
[*]~/.bash_login
[*]~/.profile
[*]~/.bashrc
[/LIST]

---

