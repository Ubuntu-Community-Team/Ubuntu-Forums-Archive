---
title: "installation of iburst driver on ubuntu 12.04"
date: 2012-07-18
forum: General Help
---

### Post by leechie on 2012-07-18
Good Day,

Have read driver installation on the forums. Have managed to unzip the driver but cannot get it to install. 

seems to be a password issue.

I am  new user

Here is the test:


geoff@geoff-Satellite-P100:~$ cd Downloads
geoff@geoff-Satellite-P100:~/Downloads$ tar -xf ibdriver*
geoff@geoff-Satellite-P100:~/Downloads$ tar -xf rp-pppoe*
geoff@geoff-Satellite-P100:~/Downloads$ dir
ibdriver-1.3.5-linux-2.6.36 rp-pppoe-3.10
ibdriver-1.3.5-linux-2.6.36.gz rp-pppoe-3.10.tar.gz
geoff@geoff-Satellite-P100:~/Downloads$ make
make: *** No targets specified and no makefile found. Stop.
geoff@geoff-Satellite-P100:~/Downloads$ sudo make install
[sudo] password for geoff:
make: *** No rule to make target `install'. Stop.
geoff@geoff-Satellite-P100:~/Downloads$ dir
ibdriver-1.3.5-linux-2.6.36 rp-pppoe-3.10
ibdriver-1.3.5-linux-2.6.36.gz rp-pppoe-3.10.tar.gz
geoff@geoff-Satellite-P100:~/Downloads$ cd ibdriver
bash: cd: ibdriver: No such file or directory
geoff@geoff-Satellite-P100:~/Downloads$ sudo
usage: sudo [-D level] -h | -K | -k | -V
usage: sudo -v [-AknS] [-D level] [-g groupname|#gid] [-p prompt] [-u user
            name|#uid]
usage: sudo -l[l] [-AknS] [-D level] [-g groupname|#gid] [-p prompt] [-U user
            name] [-u user name|#uid] [-g groupname|#gid] [command]
usage: sudo [-AbEHknPS] [-C fd] [-D level] [-g groupname|#gid] [-p prompt] [-u
            user name|#uid] [-g groupname|#gid] [VAR=value] [-i|-s] [<command>]
usage: sudo -e [-AknS] [-C fd] [-D level] [-g groupname|#gid] [-p prompt] [-u
            user name|#uid] file ...
geoff@geoff-Satellite-P100:~/Downloads$ make sudo make install
make: *** No rule to make target `sudo'. Stop.
geoff@geoff-Satellite-P100:~/Downloads$ 

appreciate any help

thanx

---

### Post by stepking2 on 2012-07-18
When you are typing make, your are in the "Downloads" directory, that's why you get "make: *** No targets specified and no makefile found. Stop."
After extraction type:

```
cd ibdriver*/ or cd ibdriver-1.3.5-linux-2.6.36\ rp-pppoe-3.10/
```But I don't think you should use that driver unless it is the latest one, because it's made for the 2.6 kernel and we are in 3.2 now.

And also, to avoid typing sudo every time, type "sudo bash" when you start the terminal.

---

