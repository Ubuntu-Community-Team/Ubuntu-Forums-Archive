---
title: "I can't change shell of root."
date: 2009-11-11
forum: General Help
---

### Post by fifoKamb3 on 2009-11-11
[FONT=Fixedsys][SIZE=2]Hi there again :)
[/SIZE][/FONT][FONT=Fixedsys][SIZE=2]I was reading chapter "shell" from the book ( Debian Tutorial Havoc Pennington) and something went wrong.
[/SIZE][/FONT][FONT=Fixedsys][SIZE=2]I did it first time and it succeeded but after that when I try to log in as root I get this:
> meem@wsLinux:~$ su root
Password: 
Cannot execute sh: No such file or directory
meem@wsLinux:~$ So I realized the mistake I did, I should give **/bin/sh** not **sh**!

I try to fix it but I get this:
> meem@wsLinux:~$ sudo chsh root
Password: 
chsh: PAM authentication failed
meem@wsLinux:~I tried with System > Administration > User and groups, but it turns back to sh instead of /bin/sh, and yes even after I restart the system.[/SIZE][/FONT]

---

### Post by Giblet5 on 2009-11-11
You'll have to boot from a live CD, mount your installed drive, and hand edit /etc/passwd on that installed drive.

I would put it back to /bin/bash, since bash is a superset of /bin/sh, and because Ubuntu was designed around certain assumptions; one of those being that root's shell is /bin/bash.

Changing root's shell is fine if you understand *everything* about:

Shells
Linux authentication
PAM authentication
/etc/passwd structure
System initialization and startup

Learning is fun. Try experimenting on a test user before hosing the superuser account: you'll spend less time reinstalling and more time learning. :)

---

