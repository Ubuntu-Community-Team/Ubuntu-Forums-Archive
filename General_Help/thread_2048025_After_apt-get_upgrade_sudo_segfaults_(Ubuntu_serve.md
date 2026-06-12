---
title: "After apt-get upgrade sudo segfaults (Ubuntu server 12.04.1)"
date: 2012-08-26
forum: General Help
---

### Post by Trikoloko on 2012-08-26
I ran sudo apt-get upgrade and noticed a number of errors. After rebooting, sudo does not work anymore. I can still log on with my user, most of the stuff works (e.g. samba shares, transmission daemon, sshd), but as sudo is dead I cannot perform any administrative task.

---

### Post by beboylips on 2012-08-26
Post the errors and what happens when you try to use sudo.

---

### Post by Trikoloko on 2012-08-26
> **beboylips said:**
> Post the errors and what happens when you try to use sudo.

Unfortunately I couldn't capture the apt-get errors (is there any log where I can do this now)?

Here is the output of a sigle sudo command (with debug information):

andgold@TheVault:~$ sudo -D 9 ls
sudo: settings: debug_level=9
sudo: settings: progname=sudo
sudo: settings: network_addrs=192.168.15.200/255.255.255.0 fe80::227:eff:fe0d:175d/ffff:ffff:ffff:ffff::
sudo: sudo_mode 1
[sudo] password for andgold:
sudo: policy plugin returns 1
sudo: command info: umask=022
sudo: command info: command=/bin/ls
sudo: command info: runas_uid=0
sudo: command info: runas_gid=0
sudo: command info: runas_groups=0
sudo: command info: closefrom=3
sudo: command info: set_utmp=true
Segmentation fault

---

### Post by Rexilion on 2012-08-26
You just found a bug in sudo (maybe) :P .

Can you post the output of:

```
dmesg | tail -n10
```

after a segfault of sudo?

---

### Post by Trikoloko on 2012-08-26
> **Rexilion said:**
> You just found a bug in sudo (maybe) :P .

Can you post the output of:

```
dmesg | tail -n10
```after a segfault of sudo?

Sure thing:

[66159.240349] init: whoopsie main process (14368) killed by SEGV signal
[66159.240433] init: whoopsie main process ended, respawning
[66159.283947] whoopsie[14373]: segfault at 7f173b2b3460 ip 00007f173b2b3460 sp 00007fff559692a8 error 14
[66159.457390] sudo[14375]: segfault at 3fa890 ip 00000000003fa890 sp 00007ffffd868218 error 14 in sudo[400000+10000]
[66159.780411] init: whoopsie main process (14373) killed by SEGV signal
[66159.780495] init: whoopsie main process ended, respawning
[66159.824390] whoopsie[14379]: segfault at 7f1192052460 ip 00007f1192052460 sp 00007fff801aa878 error 14
[66160.344401] init: whoopsie main process (14379) killed by SEGV signal
[66160.344486] init: whoopsie main process ended, respawning
[66160.388898] whoopsie[14384]: segfault at 7ff142613460 ip 00007ff142613460 sp 00007fffdfb160a8 error 14

---

### Post by Rexilion on 2012-08-27
What the hell is whoopsie? Was my first thought. It's your crash reporter.

It's not sudo that is crashing, it's 'whoopsie' (what a name...).

Sudo is working just fine =) . Don't know why it doesn't function though.

---

