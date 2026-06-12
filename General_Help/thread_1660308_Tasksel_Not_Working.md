---
title: "Tasksel Not Working"
date: 2011-01-05
forum: General Help
---

### Post by PsyclonJohn on 2011-01-05
Hello, 

Today I've had the idea to install a mail server via Tasksel and it wouldn't load up correctly.

When I type in 'Sudo Tasksel' into the terminal, I receive the error stating "debconf failed to run". I tried re-installing Tasksel, but it says that I am running the latest installation. 

Can anyone help me fix this? Or know a different way to install a mail server?

Thank you!

---

### Post by PsyclonJohn on 2011-01-05
Sorry for double posting, but I've tried something else. Still receiving a error, but maybe it will help solve the problem.

john@ubuntu:~$ sudo tasksel install mail-server
[sudo] password for john: 
Can't call method "set" on an undefined value at /usr/share/perl5/Debconf/FrontEnd.pm line 126, <GEN0> line 5.
Use of uninitialized value $ret in scalar chomp at /usr/share/perl5/Debconf/Client/ConfModule.pm line 132, <STDIN> line 4.
Use of uninitialized value $ret in split at /usr/share/perl5/Debconf/Client/ConfModule.pm line 133, <STDIN> line 4.
Use of uninitialized value $ret[0] in string eq at /usr/share/perl5/Debconf/Client/ConfModule.pm line 134, <STDIN> line 4.
Use of uninitialized value $ret[0] in string eq at /usr/bin/debconf-apt-progress line 173, <STDIN> line 4.
tasksel: aptitude failed (9)

---

### Post by Maarek Stele on 2011-06-15
> **PsyclonJohn said:**
> Hello, 

Today I've had the idea to install a mail server via Tasksel and it wouldn't load up correctly.

When I type in 'Sudo Tasksel' into the terminal, I receive the error stating "debconf failed to run". I tried re-installing Tasksel, but it says that I am running the latest installation. 

Can anyone help me fix this? Or know a different way to install a mail server?

Thank you!

Try installing tasksel.
```
$sudo apt-get install tasksel
```
Agree to the installation and then try the application.

---

### Post by WorMzy on 2011-06-15
As far as I know, tasksel has been dropped from the default packages due to a problem with it uninstalling /everything/ when told to remove package groups (e.g. lamp-server).

Instead, you should use apt-get. The package groups still exist, but you need to call them with a caret (^).

e.g.

```
sudo apt-get install lamp-server^
```

---

