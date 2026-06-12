---
title: "Update environment variables forever"
date: 2010-04-07
forum: General Help
---

### Post by anTux on 2010-04-07
Hi. I've created a new environment variable and updated another one (PATH). I just want to save this changes once after reboot and forever.

This is because I want to run a program (tecplot) just typing 'tec360' in the command line. If I create those new variable ( TEC_360_2008=/usr/tec360_2008 ) and update the PATH variable ( export PATH=$PATH:$TEC_360_2008/bin ) then bash detect the command 'tec360' and it runs my program. The problem is that this changes are not saved after rebooting.

According to the manual, I have to update the .bash_profile in my home directory but I don't have this file in this directory (neither in other directory). I only have .bash_history, .bash_logout and .bashrc in the home directory. I have updated .bashrc (typing . ./.bashrc) but it is not working...

I have Ubuntu 9.04

Can anyone help me? 
Thank you

---

### Post by cjhabs on 2010-04-07
> **anTux said:**
> Hi. I've created a new environment variable and updated another one (PATH). I just want to save this changes once after reboot and forever.

This is because I want to run a program (tecplot) just typing 'tec360' in the command line. If I create those new variable ( TEC_360_2008=/usr/tec360_2008 ) and update the PATH variable ( export PATH=$PATH:$TEC_360_2008/bin ) then bash detect the command 'tec360' and it runs my program. The problem is that this changes are not saved after rebooting.

According to the manual, I have to update the .bash_profile in my home directory but I don't have this file in this directory (neither in other directory). I only have .bash_history, .bash_logout and .bashrc in the home directory. I have updated .bashrc (typing . ./.bashrc) but it is not working...

I have Ubuntu 9.04

Can anyone help me? 
Thank you

If you replace the current PATH definition in .bashrc with:
export PATH=$PATH:$TEC_360_2008/bin
this will make it permanent.

Is this what you did and it is not working for you?
If that is the case, I can only assume you are not using bash as your login shell.

---

### Post by anTux on 2010-04-07
I just added this line in .bashrc and it works":P
Thank you very much!!
By the way, I still don't know why I don't have the .bash_profile

---

### Post by cjhabs on 2010-04-07
Maybe this will explain it:
[http://joshstaiger.org/archives/2005/07/bash_profile_vs.html](http://joshstaiger.org/archives/2005/07/bash_profile_vs.html)

I don't have one either.

---

### Post by dcstar on 2010-04-07
> **anTux said:**
> Hi. I've created a new environment variable and updated another one (PATH). I just want to save this changes once after reboot and forever.

This is because I want to run a program (tecplot) just typing 'tec360' in the command line. If I create those new variable ( TEC_360_2008=/usr/tec360_2008 ) and update the PATH variable ( export PATH=$PATH:$TEC_360_2008/bin ) then bash detect the command 'tec360' and it runs my program. The problem is that this changes are not saved after rebooting.
.......

If you want a global path setting change:

```
gksudo gedit /etc/environment
```

---

### Post by drreed on 2010-04-15
> **dcstar said:**
> If you want a global path setting change:

```
gksudo gedit /etc/environment
```

Thanks

---

