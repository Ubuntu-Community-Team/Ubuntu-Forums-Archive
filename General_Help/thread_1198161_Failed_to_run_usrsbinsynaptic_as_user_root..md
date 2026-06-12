---
title: "Failed to run /usr/sbin/synaptic as user root."
date: 2009-06-27
forum: General Help
---

### Post by GnrPersia on 2009-06-27
Hi,

before I write my problem I wanted to say that I've been using windows for my entire life and it's just 3 days that I've just decided to completely get out of windows and start to work with ubuntu.

so far everything was fine until today after updating something and messing around with "gksudo" commands restarted my comp and now I get this problem when I want to run synaptic package manager that a window appears with the following comments:

[B]"Failed to run /usr/sbin/synaptic as user root.

The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator."[/B]

something is not letting me even go to system > users and groups as well as lots of other places. 

also I thought that this might be useful to help me in the case:

in terminal:

[b]adel@aDell:~$ sudo synaptic package manager
[sudo] password for adel: 
adel is not in the sudoers file.  This incident will be reported.[/b]


Please help me because I don't want to get disappointed with this one and step back to windows. :(


many thanks

Adel

---

### Post by Soul-Sing on 2009-06-27
: [http://ubuntuforums.org/archive/index.php/t-334022.html](http://ubuntuforums.org/archive/index.php/t-334022.html)

is very helpful imo.
you have to edit sudoers, to set the permissions allright.

---

### Post by Elfy on 2009-06-27
Please do not post post duplicates - [http://ubuntuforums.org/showthread.php?t=1198166](http://ubuntuforums.org/showthread.php?t=1198166)

---

