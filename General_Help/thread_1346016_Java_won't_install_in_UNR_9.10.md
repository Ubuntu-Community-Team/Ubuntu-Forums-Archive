---
title: "Java won't install in UNR 9.10"
date: 2009-12-04
forum: General Help
---

### Post by Chief_runningwater on 2009-12-04
So I recently installed Ubuntu Netbook Remix 9.10 on my Asus 1005HA and it's amazing, works perfectly and all but when I try and install any type of java from the add/remove panel I always get this error when the package gets to 3%

So how do I fix this because I want to install Java runtime files.

[[IMG]http://i183.photobucket.com/albums/x91/Googler69/th_Screenshot.png[/IMG]](http://s183.photobucket.com/albums/x91/Googler69/?action=view&current=Screenshot.png)

---

### Post by bunk3rk1ng on 2009-12-04
I'm new as well, so this is just a shot in the dark.

I got java through the Ubuntu restricted extras package.

```
$sudo apt-get install ubuntu-restricted-extras
```I actually had an error during that and needed to install Java again.  So I used:
```
$sudo apt-get install sun-java6-bin
```Good luck :D

---

### Post by Chief_runningwater on 2009-12-04
> **bunk3rk1ng said:**
> I'm new as well, so this is just a shot in the dark.

I got java through the Ubuntu restricted extras package.

```
$sudo apt-get install ubuntu-restricted-extras
```I actually had an error during that and needed to install Java again.  So I used:
```
$sudo apt-get install sun-java6-bin
```Good luck :D

I tried both and got 

```
nicholas@nicholas-laptop:~$ $sudo apt-get install sun-java6-bin
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
nicholas@nicholas-laptop:~$
```

---

### Post by bunk3rk1ng on 2009-12-04
> **Chief_runningwater said:**
> I tried both and got 

```
nicholas@nicholas-laptop:~$ $sudo apt-get install sun-java6-bin
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
nicholas@nicholas-laptop:~$
```

I just tried on my machine and got the same error.  Don't put the extra '$'.

It should be:

> nicholas@nicholas-laptop:~$sudo apt-get install sun-java6-binSame goes for all commands :D

---

### Post by Chief_runningwater on 2009-12-04
> **bunk3rk1ng said:**
> I just tried on my machine and got the same error.  Don't put the extra '$'.

It should be:

Same goes for all commands :D

Not 100% what I did but I can't remove it and when i try the command without the $ it gives me

```
nicholas@nicholas-laptop:~$ sudo apt-get install ubuntu-restricted-extras
[sudo] password for nicholas: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ubuntu-restricted-extras is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package ubuntu-restricted-extras has no installation candidate
nicholas@nicholas-laptop:~$

```

---

### Post by bunk3rk1ng on 2009-12-04
> **Chief_runningwater said:**
> Not 100% what I did but I can't remove it and when i try the command without the $ it gives me

```
nicholas@nicholas-laptop:~$ sudo apt-get install ubuntu-restricted-extras
[sudo] password for nicholas: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ubuntu-restricted-extras is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package ubuntu-restricted-extras has no installation candidate
nicholas@nicholas-laptop:~$

```

It sounds like something is wrong with your repositories.

Can you post what is in /etc/apt/sources.list ?

---

### Post by Chief_runningwater on 2009-12-04
Thanks for the help I figured it out, I messed with the repositories and I guess screwed it up so I reverted it back to default and now it's working.

---

