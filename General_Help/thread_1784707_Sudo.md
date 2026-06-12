---
title: "Sudo"
date: 2011-06-17
forum: General Help
---

### Post by hewjr1000 on 2011-06-17
Just did a fresh install of Ubuntu 10.10 sudo not working.

This is the message I get.

hewjr@Hewjr:~$ sudo
usage: sudo -h | -K | -k | -L | -V
usage: sudo -v [-AknS] [-p prompt]
usage: sudo -l[l] [-AknS] [-g groupname|#gid] [-p prompt] [-U username] [-u username|#uid] [-g groupname|#gid] [command]
usage: sudo [-AbEHknPS] [-C fd] [-g groupname|#gid] [-p prompt] [-u username|#uid] [-g groupname|#gid] [VAR=value] [-i|-s] [<command>]
usage: sudo -e [-AknS] [-C fd] [-g groupname|#gid] [-p prompt] [-u username|#uid] file ...
hewjr@Hewjr:~$

Henry

---

### Post by Elfy on 2011-06-17
Do you get that if you run a command with sudo? 

For example sudo apt-get update

---

### Post by MacHackers on 2011-06-17
> **hewjr1000 said:**
> Just did a fresh install of Ubuntu 10.10 sudo not working.

This is the message I get.

hewjr@Hewjr:~$ sudo
usage: sudo -h | -K | -k | -L | -V
usage: sudo -v [-AknS] [-p prompt]
usage: sudo -l[l] [-AknS] [-g groupname|#gid] [-p prompt] [-U username] [-u username|#uid] [-g groupname|#gid] [command]
usage: sudo [-AbEHknPS] [-C fd] [-g groupname|#gid] [-p prompt] [-u username|#uid] [-g groupname|#gid] [VAR=value] [-i|-s] [<command>]
usage: sudo -e [-AknS] [-C fd] [-g groupname|#gid] [-p prompt] [-u username|#uid] file ...
hewjr@Hewjr:~$

Henry
That is normal. **_You can't use sudo by itself._** If you need root access in the terminal type: **sudo su** and if required, type in your account password.
 
Hope it helps!

---

### Post by MacHackers on 2011-06-17
> **forestpiskie said:**
> Do you get that if you run a command with sudo? 

For example sudo apt-get update
I agree with your post....
 
**Again, you can't run sudo by itself, but if it is doing that when you are running a command, something isn't right.**

---

### Post by MacHackers on 2011-06-17
> **hewjr1000 said:**
> Just did a fresh install of Ubuntu 10.10 sudo not working.

This is the message I get.

hewjr@Hewjr:~$ sudo
usage: sudo -h | -K | -k | -L | -V
usage: sudo -v [-AknS] [-p prompt]
usage: sudo -l[l] [-AknS] [-g groupname|#gid] [-p prompt] [-U username] [-u username|#uid] [-g groupname|#gid] [command]
usage: sudo [-AbEHknPS] [-C fd] [-g groupname|#gid] [-p prompt] [-u username|#uid] [-g groupname|#gid] [VAR=value] [-i|-s] [<command>]
usage: sudo -e [-AknS] [-C fd] [-g groupname|#gid] [-p prompt] [-u username|#uid] file ...
hewjr@Hewjr:~$

Henry
Try and run the following commands to help fix it (if it does this when you run a command)...
 
**sudo su **(gives you root access)
[B]sudo dpkg --configure -a
**sudo apt-get update**
**sudo apt-get upgrade**
 
[/B]

---

### Post by hewjr1000 on 2011-06-17
Thanks for all your replies. I forgot to include command.

---

### Post by Elfy on 2011-06-17
> **hewjr1000 said:**
> Thanks for all your replies. I forgot to include command.

Makes all the difference - I assume all is well now. Please mark thread solved if it is - Thread Tools at the top.

---

### Post by sisco311 on 2011-06-17
> **MacHackers said:**
> That is normal. **_You can't use sudo by itself._** If you need root access in the terminal type: **sudo su** and if required, type in your account password.


Of course you can. Invoked with -i or -s sudo starts a root shell. The preferred method is **sudo -i**. See: [uhelp]community/RootSudo[/uhelp]

---

### Post by Elfy on 2011-06-17
Thanks sisco311 - missed all those sudo su's ... hunger is my excuse.

@ MacHackers - please see [http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138) in addition to the link in post #8

---

