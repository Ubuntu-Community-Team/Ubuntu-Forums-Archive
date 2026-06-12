---
title: "Environment variable setting help"
date: 2010-12-19
forum: General Help
---

### Post by programmer89 on 2010-12-19
Hey People! :) Am new here. Have been using ubuntu since a few months...

Ok now i have created a .bash_profile file in my **/home/<acc_name>/** folder. The problem is that everytime i login to that <acc_name> using my terminal, i have to execute the .bash_profile file evertime to get my commands to work.. Why is it like that? Am i editing the wrong file or is the .bash_profile file in the wrong location?? The .profile file is in the same location by default i believe..

ok here's the code in which you can see my sqlplus command wont work until i execute the .bash_profile file...


```
stoned_420@stoners:~$ su oracle
Password: 
oracle@stoners:/home/stoned_420$ cd ~
oracle@stoners:~$ rlwrap sqlplus
rlwrap: Cannot execute sqlplus: No such file or directory
oracle@stoners:~$ . .bash_profile
oracle@stoners:~$ rlwrap sqlplus

SQL*Plus: Release 10.2.0.1.0 - Production on Sun Dec 19 21:41:23 2010

Copyright (c) 1982, 2005, Oracle.  All rights reserved.

Enter user-name: sys as sysdba
Enter password: 
```

Any help would be highly appreciated..

I LOVE LINUX!! :D :popcorn:

---

### Post by gmargo on 2010-12-19
If it's an environment variable or a $PATH change, you are better off adding it to the end of $HOME/.profile instead of using .bash_profile.

---

### Post by programmer89 on 2010-12-21
> **gmargo said:**
> If it's an environment variable or a $PATH change, you are better off adding it to the end of $HOME/.profile instead of using .bash_profile.

Whats this supposed to mean??


```
# ~/.profile: executed by the command interpreter for login shells.
# This file is not read by bash(1), if ~/.bash_profile or ~/.bash_login
# exists.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.
```

And i tried adding the lines to the .profile fie.. Still it wont help.... I need to execute .profile too everytime...!!!

Btw this is my .bash_profile file...


```
oracle@stoners:~$ cat .bash_profile
export ORACLE_SID=abhi
export ORACLE_HOME=/home/oracle/oracle/product/10.2.0/db_1

export PATH=$ORACLE_HOME/bin:$PATH
export LD_LIBRARY_PATH=$ORACLE_HOME/lib
```

---

### Post by programmer89 on 2010-12-23
bump anyone?? :(

---

### Post by Habitual on 2010-12-23
try 'su **-** oracle' instead to load up the oracle user's environment when you su to it.

---

### Post by programmer89 on 2010-12-24
> **Habitual said:**
> try 'su **-** oracle' instead to load up the oracle user's environment when you su to it.

Dude you rock!! Thanx man!

What actually does the '-' function do?? Run the .profile or .bash_profile file is it?

---

### Post by KiLaHuRtZ on 2010-12-24
Place the lines in *.bashrc* in your home directory.

---

