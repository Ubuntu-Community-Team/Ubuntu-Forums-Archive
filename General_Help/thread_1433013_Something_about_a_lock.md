---
title: "Something about a lock?"
date: 2010-03-18
forum: General Help
---

### Post by atothec on 2010-03-18
Hi all,

I downloaded Ubuntu 9.10 today and installed it on a virtual machine. I tried running the command
[FONT=Verdana]sudo apt-get install ghc6 gnat clisp sun-java6-jdk swi-prolog gcc python[/FONT]

[FONT=Verdana]however when I run it I get the following errors:
[/FONT][FONT=Verdana]
[FONT=Verdana]E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the list directory

I have no idea what I am supposed to do. This is the first time I have installed Linux.
[/FONT][/FONT]

---

### Post by howefield on 2010-03-18
You have another package manager running, whether that be apt-get, Software Center, Update Manager, Synaptic Package Manager, Adept Package Manager, ect ect.

You can only have one package manager running at a time.

Try closing all package managers or if that doesn't work, reboot and try again. ?

---

### Post by wdaniels on 2010-03-18
You must have some other package manager open or running at the same time. Only one app may install software via apt at any time. If you have Synaptic open then close it, because it locks apt even if it's not actually doing anything at the time (well, last I remember using it that was the case).

---

### Post by atothec on 2010-03-18
I rebooted Ubuntu and type sudo apt-get update and it seems to be doing something. If the sudo command I mentioned doesn't work I'll let you know ;)

Btw, what does sudo mean?

---

### Post by mcduck on 2010-03-18
> **atothec said:**
> I rebooted Ubuntu and type sudo apt-get update and it seems to be doing something. If the sudo command I mentioned doesn't work I'll let you know ;)

Btw, what does sudo mean?

"Substitute User DO". It's used to execute commands as other users (if you specify no user then it runs the command as root user).

---

### Post by wdaniels on 2010-03-18
> **atothec said:**
> I rebooted Ubuntu and type sudo apt-get update and it seems to be doing something.

Ah yes, actually if it's /var/lib/apt/lists/lock then that is specifically the package *indexes* that are locked, which would only be apt-get update. You can always check which process has locked a file with the lsof command:

```
sudo lsof /var/lib/apt/lists/lock
```

sudo just runs your command with elevated privileges, usually "root" privileges. The root user is equivalent to the Windows "Administrator" user. But unlike most Windows setups, Ubuntu does not run with these privileges all the time, which is better for security.

---

### Post by atothec on 2010-03-18
Euxapisto :D

---

### Post by rnerwein on 2010-03-18
> **atothec said:**
> Hi all,

I downloaded Ubuntu 9.10 today and installed it on a virtual machine. I tried running the command
[FONT=Verdana]sudo apt-get install ghc6 gnat clisp sun-java6-jdk swi-prolog gcc python[/FONT]

[FONT=Verdana]however when I run it I get the following errors:
[/FONT][FONT=Verdana]
[FONT=Verdana]E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the list directory

I have no idea what I am supposed to do. This is the first time I have installed Linux.
[/FONT][/FONT]

hi
open a terminal and change to the directory: [FONT=Verdana][FONT=Verdana] /var/lib/apt/lists
then run: sudo fuser -u lock
this will show you the PID of the process which holds the lock.
then: ps -ef | gerp PID  - this will give you the process.
ciao
[/FONT][/FONT]

---

### Post by wdaniels on 2010-03-18
> **atothec said:**
> Euxapisto :D

parakalw ;)
eiste ellinas;

PS: I'm English anyway :D

---

### Post by atothec on 2010-03-18
Kypraios lol. I'm English too :D

---

### Post by atothec on 2010-03-18
Everything looks like it's working, thanks a lot guys :)

---

