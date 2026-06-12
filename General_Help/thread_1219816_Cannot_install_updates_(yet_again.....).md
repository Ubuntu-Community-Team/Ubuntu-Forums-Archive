---
title: "Cannot install updates (yet again.....)"
date: 2009-07-22
forum: General Help
---

### Post by The Toxic Mite on 2009-07-22
Hey all.

I recently got my wireless to work, but before that, I had to use my phone to update all the software sources.


Now, I can't install any updates. I only have the default sources active. I tried reloading the sources but I still can't update.

Here's the results of "sudo apt-get dist-upgrade":

```
calvinps@InterCity-125:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
[snip/]
169 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
[B]E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory[/B]
calvinps@InterCity-125:~$ 

```

The same errors are happening on update-manager as well. The screenshot's attached.

-TTM-

---

### Post by bacil on 2009-07-22
did you try to run apt-get as well as update manager in the same time ?

can you run

```
ls -l /var/cache/apt/archives
```just to make sure that directory exits ?

and one more

```
fuser /var/cache/apt/archives/lock
```

to see if any process is hanging on the lock

---

### Post by The Toxic Mite on 2009-07-22
```
calvinps@InterCity-125:~$ ls -l /var/cache/apt/archives
total 4
-rw-r----- 1 root root    0 2009-04-20 15:00 lock
drwxr-xr-x 2 root root 4096 2009-04-20 15:09 **[COLOR=MediumTurquoise]partial[/COLOR]**

```

---

### Post by bacil on 2009-07-22
and fuser ?

---

### Post by philinux on 2009-07-22
You can only have 1 package manager working at a time as it get a lock.

Why you running dist-upgrade, are you running Karmic Koala?

---

### Post by The Toxic Mite on 2009-07-22
```

calvinps@InterCity-125:~$ fuser -l /var/cache/apt/archives
HUP INT QUIT ILL TRAP ABRT IOT BUS FPE KILL USR1 SEGV USR2 PIPE ALRM TERM
STKFLT CHLD CONT STOP TSTP TTIN TTOU URG XCPU XFSZ VTALRM PROF WINCH IO PWR SYS
UNUSED

```

I think I did it wrong :oops:

---

### Post by The Toxic Mite on 2009-07-22
> **philinux said:**
> You can only have 1 package manager working at a time as it get a lock.

Why you running dist-upgrade, are you running Karmic Koala?

No, I am using Jaunty Jackalope (9.04).

I still can't install anything, I get exactly the same errors as I explained on the original post.

I tried to install ubuntu-restricted-extras using the terminal, but it didn't work for reasons I explained above. No other package manager was in use.

---

### Post by The Toxic Mite on 2009-07-22
> **bacil said:**
> did you try to run apt-get as well as update manager in the same time ?

can you run

```
ls -l /var/cache/apt/archives
```just to make sure that directory exits ?

and one more

```
fuser /var/cache/apt/archives/lock
```to see if any process is hanging on the lock

It says nothing when I do the fuser command you describe above

---

### Post by philinux on 2009-07-22
I assume you rebooted?

---

### Post by bacil on 2009-07-22
Yes you have it wrong :-)

```
fuser /var/cache/apt/archives/lock
```

you want to see what process is hanging on the lock. why your apt-can not obtain it

---

### Post by The Toxic Mite on 2009-07-22
> **bacil said:**
> Yes you have it wrong :-)

```
fuser /var/cache/apt/archives/lock
```you want to see what process is hanging on the lock. why your apt-can not obtain it

It says nothing when I do that command

---

