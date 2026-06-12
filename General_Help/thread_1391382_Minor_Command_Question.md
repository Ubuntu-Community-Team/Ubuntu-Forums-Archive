---
title: "Minor Command Question"
date: 2010-01-26
forum: General Help
---

### Post by MadDawg010 on 2010-01-26
Can anyone explain exactly what the command below does?

```
sudo aptitude purge `dpkg -l | grep "^rc" | tr -s ' ' | cut -d ' ' -f 2`
```

I found this "super clean" command while looking up the difference between clean and autoclean. I used this to reclaim some space, and it did so quite well. I want to recommend this to users, but I need to be able to fully explain what this does; I don't want to just tell a user to throw this into their terminal prompt without letting them know exactly what happens.

---

### Post by warfacegod on 2010-01-26
If you don't want to recommend it with out understanding it entirely then why would you use it on your own system?

---

### Post by MadDawg010 on 2010-01-26
I have a virtual machine I can test unusual commands on, so if I nuke the VM, nothing is lost.

---

### Post by warfacegod on 2010-01-26
I would opena Terminal Type "man" bfore each part of the code, Example:

```
man grep
``` Enter. man is short for manual and will give a description of each command.

---

### Post by sisco311 on 2010-01-26
sudo = run the command as root
aptitude = package manager
purge = purge package
`command` or $(command) = replace command name with the output of the command
```
man bash | less +/"Command Substitution"
```
dpkg -l = list packages
dpkg -l | grep "^rc" = list only the lines which begin with *rc*  
dpkg -l | grep "^rc" | tr -s ' ' | cut -d ' ' -f 2 = list only the second column (package name) of the lines

---

### Post by gnack on 2010-01-26
Another version:

sudo aptitude purge `dpkg -l | grep '^rc' | awk '{print $2}'`

dpkg -l lists all packages installed or otherwise; the first two columns of each line indicate that packages state:

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/

So, grep '^rc' says find the lines with "rc" at the beginning - the desired action is "Remove" and the status is "Cfg-files" (only config files exist on the system).  For example:

rc  nvidia-glx-180     180.44-0ubuntu1   NVIDIA binary Xorg driver
rc  nvidia-settings    180.25-0ubuntu1   Tool of configuring the NVIDIA... 

The tr/cut or awk command just grabs the package name (nvidia-settings)

aptitude purge removes the package/config from the system

---

### Post by audiomick on 2010-01-26
I would have suggested the same as warfacegod.

---

### Post by MadDawg010 on 2010-01-26
Awesome, thanks sisco311. I was a little confused after reading all the manual entries for the separate commands.

Thanks for your input as well, warfacegod. I had somehow managed to completely forget about the **man** command. I guess this is what school does to me.

This thread is solved.

---

### Post by gnack on 2010-01-26
And adding an -s to the aptitude command will simulate the purge just in case you're unsure:

sudo aptitude -s purge ...

---

### Post by MadDawg010 on 2010-01-26
Ah, thanks for the additional input, gnack.

---

### Post by sisco311 on 2010-01-26
> **gnack said:**
> Another version:

sudo aptitude purge `dpkg -l | grep '^rc' | awk '{print $2}'`



if you use awk, then use it properly. :evil:
```
sudo aptitude purge $(dpkg -l | awk '$1=="rc"{print $2}')
```
:)

---

