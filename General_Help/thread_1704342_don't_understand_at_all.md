---
title: "don't understand at all"
date: 2011-03-10
forum: General Help
---

### Post by dunkslayer on 2011-03-10
root@mail:/home/silent/Downloads/iRedMail-0.6.1/pkgs# bash get_all.sh
< INFO > Creating necessary directories ...
< INFO > ==================== Fetching Source Tarballs ====================
< INFO > * 1/5: [http://iredmail.org/apt/misc/postfixadmin_2.3.tar.gz](http://iredmail.org/apt/misc/postfixadmin_2.3.tar.gz)
< INFO > * 2/5: [http://iredmail.org/apt/misc/iRedAdmin-0.1.3.tar.bz2](http://iredmail.org/apt/misc/iRedAdmin-0.1.3.tar.bz2)
< INFO > * 3/5: [http://iredmail.org/apt/misc/iRedAPD-1.3.3.tar.bz2](http://iredmail.org/apt/misc/iRedAPD-1.3.3.tar.bz2)
< INFO > * 4/5: [http://iredmail.org/apt/misc/roundcubemail-0.3.1.tar.gz](http://iredmail.org/apt/misc/roundcubemail-0.3.1.tar.gz)
< INFO > * 5/5: [http://iredmail.org/apt/misc/phpldapadmin-1.2.0.5.tgz](http://iredmail.org/apt/misc/phpldapadmin-1.2.0.5.tgz)
< INFO > Validate Packages ...    [ OK ]
< INFO > Checking necessary command/package: dialog/dialog ...
< INFO > Installing package(s): dialog
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package dialog is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'dialog' has no installation candidate
< ERROR > Installation failed, please check the terminal output.


what's the meaning of all these....plis somebody help me...thanks in advance:(

---

### Post by lithopsian on 2011-03-10
Do apt-cache policy dialog and post the output.  It should be a valid package but perhaps not the version you need.  Which Ubuntu do you have?  Have you upgraded it from an earlier version?  Do you know which version of dialog is attempting to be installed?

---

### Post by oldos2er on 2011-03-10
It's looking for a package named 'dialog', which doesn't seem to exist. I suggest you try iredmail's forum where you're more likely to get help: [http://iredmail.org/forum/](http://iredmail.org/forum/)

---

### Post by WorMzy on 2011-03-10
The dialog package exists in the repos. Install it with
```
apt-get install dialog
```

(Note that you will need to append "sudo" to the start of that command if you run it as a normal, non-root user)

---

### Post by dunkslayer on 2011-03-10
im runnin ubuntu version 10.10 32bit on VMware...iredmail version is 0.6,1...

i already try  the code "apt-get dialog" but still the same result appear...

what do you guys think the problem is...?ubuntu or iredmail...??

im very new with linux based system..start using it for 1 month now...plis forgive me if im asking a very silly question here guys...

thanks a lot for those who reply towards my question... :D

---

### Post by 3rdalbum on 2011-03-11
The program's website says it only supports 10.04, not 10.10. The 'dialog' package might not be available in 10.10 anymore.

---

### Post by doas777 on 2011-03-11
you do have the universe repositories enabled, right?

it should be there:
[http://packages.ubuntu.com/maverick/dialog](http://packages.ubuntu.com/maverick/dialog)

try 
```
sudo apt-get update && sudo apt-get install dialog
```and try again.
if all else fails, download the source from above (right hand side), and [compile/install]("https://help.ubuntu.com/community/CompilingEasyHowTo") it.

---

### Post by dunkslayer on 2011-03-11
thanks a lot for "3rdalbum" and "doas777"...really appreciate it guys... :D

the iredmail forum doesn't seem to help me enough...

---

