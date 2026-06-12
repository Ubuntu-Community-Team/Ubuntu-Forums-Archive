---
title: "System Information"
date: 2010-09-24
forum: General Help
---

### Post by GrumpyBum on 2010-09-24
Hi All,

I have searched but cannot find a command to display the system load information that is displayed at logon on a command only server. I am running Ubuntu 10.04.1 server and this would help.

Can anyone please tell me what the command to display this information (as follows) is?

```
System information as of Sat Sep 25 11:56:14 EST 2010

  System load:  0.58              Processes:           94
  Usage of /:   6.3% of 37.97GB   Users logged in:     0
  Memory usage: 43%               IP address for eth0: 192.168.84.84
  Swap usage:   0%

  Graph this data and manage this system at https://landscape.canonical.com/
```

The full screen displayed wit this is,

```
Linux UBUNTULAMP001 2.6.32-24-generic-pae #43-Ubuntu SMP Thu Sep 16 15:30:27 UTC 2010 i686 GNU/Linux
Ubuntu 10.04.1 LTS

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

  System information as of Sat Sep 25 11:56:14 EST 2010

  System load:  0.58              Processes:           94
  Usage of /:   6.3% of 37.97GB   Users logged in:     0
  Memory usage: 43%               IP address for eth0: 192.168.84.84
  Swap usage:   0%

  Graph this data and manage this system at https://landscape.canonical.com/

Last login: Sat Sep 25 10:53:38 2010 from 192.168.84.72
```

I have tried using 'sysinfo' but this will not run without a GUI.

Many Thanks,

---

### Post by andrewthomas on 2010-09-24
```
top 
```is similar

---

### Post by GrumpyBum on 2010-09-25
'top' is perfect thank you

---

