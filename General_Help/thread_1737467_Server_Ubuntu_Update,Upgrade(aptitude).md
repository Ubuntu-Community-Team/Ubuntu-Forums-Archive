---
title: "Server Ubuntu Update,Upgrade(aptitude)"
date: 2011-04-23
forum: General Help
---

### Post by Coldrake on 2011-04-23
Hi.. i'm new in this comunity,i have a litle question..and here i go!

```
Linux skynet 2.6.32-31-generic-pae #61-Ubuntu SMP Fri Apr 8 20:00:13 UTC 2011 i686 GNU/Linux
Ubuntu 10.04.2 LTS

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

  System information as of Sat Apr 23 12:48:24 CLST 2011

  System load:  0.21              Temperature:         30 C
  Usage of /:   1.5% of 72.14GB   Processes:           100
  Memory usage: 2%                Users logged in:     0
  Swap usage:   0%                IP address for eth0: 192.168.0.5

  Graph this data and manage this system at https://landscape.canonical.com/

Ubuntu 10.04.2 LTS

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

 System information disabled due to load higher than 1

40 packages can be updated.
17 updates are security updates.

Last login: Sat Apr 23 12:40:20 2011 from 192.168.0.3

```

i do ```
sudo aptitude update
```
then ```
sudo aptitude safe-upgrade
``` and ```
sudo aptitude full-upgrade
```..

[SIZE="3"][COLOR="Red"]40 packages can be updated.
17 updates are security updates.[/COLOR][/SIZE]


and i reboot the machine,and throw me the same notice.

thanks everyone!!

---

### Post by scarf on 2011-05-11
i have this problem too.  it seems to repeat the login message but one of the messages still has the old update info in it....

---

### Post by mothy_jim on 2011-05-12
I too am getting this running the server version 10.04.LTS

Terminal output follows with repeated login text in red:

```
Linux ubuntu-server-1 2.6.32-30-server #59-Ubuntu SMP Tue Mar 1 22:46:09 UTC 2011 x86_64 GNU/Linux
Ubuntu 10.04.2 LTS

Welcome to the Ubuntu Server!
 * Documentation:  http://www.ubuntu.com/server/doc

  System information as of Thu May 12 07:32:01 BST 2011

  System load:    0.09               Processes:             132
  Usage of /home: 10.7% of 48.06GB   Users logged in:       1
  Memory usage:   8%                 IP address for eth0:   10.0.0.210
  Swap usage:     0%                 IP address for virbr0: 192.168.122.1

  Graph this data and manage this system at https://landscape.canonical.com/

[COLOR=Red]Ubuntu 10.04.2 LTS

Welcome to the Ubuntu Server![/COLOR] [COLOR=Red]
 * Documentation:  http://www.ubuntu.com/server/doc

[/COLOR] [COLOR=Red]   System information as of Tue Apr 19 23:29:56 BST 2011

[/COLOR] [COLOR=Red]   System load:    0.0               Processes:             121
  Usage of /home: 8.6% of 48.06GB   Users logged in:       0
  Memory usage:   22%               IP address for eth0:   10.0.0.210
  Swap usage:     0%                IP address for virbr0: 192.168.122.1

[/COLOR] [COLOR=Red]   Graph this data and manage this system at https://landscape.canonical.com/

19 packages can be updated.[/COLOR] [COLOR=Red]
0 updates are security updates.
[/COLOR] 
Last login: Thu May 12 07:30:32 2011

```

---

### Post by plucky on 2011-05-12
This [link](http://ubuntuforums.org/showthread.php?t=1737625) might help.

[Bug Report](https://bugs.launchpad.net/ubuntu/+source/pam/+bug/766827)

Good Luck

---

### Post by mothy_jim on 2011-05-12
Thanks Plucky, that worked for me!

---

