---
title: "Booting into console"
date: 2009-10-03
forum: General Help
---

### Post by yun4 on 2009-10-03
Hi, I'm trying to get ubuntu 9.10 to boot into console by default and tried a number of solutions still with no success.

I've tried ```
sudo sysv-rc-conf --level 0123456 gdm off
``` & ```
sudo update-rc.d -f gdm remove
```

Any suggestions?

---

### Post by Primefalcon on 2009-10-03
> **yun4 said:**
> Hi, I'm trying to get ubuntu 9.10 to boot into console by default and tried a number of solutions still with no success.

I've tried ```
sudo sysv-rc-conf --level 0123456 gdm off
``` & ```
sudo update-rc.d -f gdm remove
```

Any suggestions?
you have to delete the file S30gdm from /etc/rc3.d/ which happens to be the run level 3 GUI or you can rename the file by putting a ~ in front of it, this way you can easily get it back

you then tell you boot from run level 3 as default by entering into the file /etc/inittab

the following line

id:3:initdefault:

after which if you need the gui you can just run startx,

or to change it back into using the gui change that last line to

id:2:initdefault which is run level 2 which was the default before this anyhow, you could probably do it to run level 4 or such as well but just 1 up from 2 is just as easy

to skip between command line start or gui start just edit the init tab file to set the run level mode and reboot

---

### Post by yun4 on 2009-10-04
Tried renaming and deleting the files with gdm on it still with no success. Checked run level, it is booted into run level 3 as specify in the inittab. 

BTW I thought ubuntu abandoned the inittab file, how is it still working?

---

### Post by yun4 on 2009-10-04
the solution worked for you warduria?

---

