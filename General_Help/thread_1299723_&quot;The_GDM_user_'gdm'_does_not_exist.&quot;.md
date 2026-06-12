---
title: "&quot;The GDM user 'gdm' does not exist.&quot;"
date: 2009-10-24
forum: General Help
---

### Post by Unsolveable on 2009-10-24
When i am starting up Ubuntu it says; 
"The GDM user 'gdm' does not exist. Please correct GDM configuration and restart GDM"





Any ways to solve this error:confused::confused::confused::confused::confused:



thanks,
           Unsolveable

---

### Post by duanedesign on 2009-10-24
I have seen a few of these posts before. There does not seem to be any one fix that I can find. If you can get to a command prompt or Terminal try running:
```
sudo apt-get install --reinstall gdm && sudo dpkg-reconfigure gdm
```

---

### Post by Unsolveable on 2009-10-25
Thanks for replying but no luck :(:(
it gets to here:
root@ubuntu-desktop:~# sudo apt-get install --reinstall gdm && sudo dpkg-reconfigure gdm

```
Reading package list... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 3 not upgraded.
Need to get 1980kB of archives.
After this operation, 0B of additional disk space will be used.
do you want to continue [Y/n]? Y
Err http://gb.archive.ubuntu.com jaunty/main gdm 2.20.10-0ubuntu2
  Could not resolve 'gb.archive.ubuntu.com'
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gdm/gd,_2.20.10-0ubuntu2_deb Could not resolve 'gb.archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
 root@ubuntu-desktop:~# _
```

---

### Post by MelDJ on 2009-10-25
type this then --fix-missing.
and just use sudo instead of sudo su, unless i am mistaken and your user name is root :)

---

### Post by Unsolveable on 2009-10-25
Hi there
No success :(:(:(
for --fix-missing I get:

```
bash: --fix-missing: command not found
```

For sudo --fix-missing I get:

```
sudo: please use single character options
usage: sudo -h | -K | -k | -L | -l | -V | -v
usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value]
            {-i | -s | <command>}
usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ...

```

Any way of fixing this ???

thanks,
           Unsolveable

---

### Post by falconindy on 2009-10-25
> ```
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```
'--fix-missing' is an option for apt-get. In other words, apt-get wants you to run it as `apt-get update --fix-missing`.

---

### Post by alving on 2009-11-10
hi all

i am having the same problem. "gdm user doesnt exist".
when i tried to type any of the above command, i get an error message saying:
"alving is not in the sudoers file. the incident will be reported."

can someone please tell me how i can fix this?

thanks

---

### Post by alving on 2009-11-12
hi again

i took my laptop to the shop today to find out what is the problem.
the end of october it did an update.
when it was finished the update it started deleting my users and groups.
when we checked the list of users it only had 2, root and alving.
all the rest have been deleted.

the tech told me it looks like someone hacked into my system.
he told me the best thing to do, is to reformat and reinstall.
he advised against trying to do an update from the root shell because it could cause more problems.
or the hacker (if thats what it was) could get back in to my system and possibly my local network.

thanks

---

