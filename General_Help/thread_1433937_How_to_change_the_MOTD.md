---
title: "How to change the MOTD?"
date: 2010-03-19
forum: General Help
---

### Post by eawedat on 2010-03-19
hey all
how to change the motd file
so i can put whatever i want
assuming am the root of the system and wanna users when log-in to their Terminal.
a specific welcoming message appears to them .
 
when i pico /etc/motd
and change
i go back to /etc/motd
i find out no changes there,
 
why ? what is the reason?
do i have to enable something ?
 
thanks.

---

### Post by uRock on 2010-03-19
On a router, terminal, server?

---

### Post by uRock on 2010-03-19
This may be what you are looking for. [http://www.howtogeek.com/howto/ubuntu/change-ssh-welcome-banner-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/change-ssh-welcome-banner-on-ubuntu/)

---

### Post by Chesamo on 2010-03-19
Pico? What, are you on OSX/FreeBSD or something?

Next question: Are you remembering to sudo? /etc/motd isn't a user-editable file; you need root permissions to do that (which sudo grants you).

---

### Post by eawedat on 2010-03-19
Find this line in the file and change the yes to no as shown:
[INDENT]PrintLastLog no
 
there is no such line
..
to add it or manually or what?
[/INDENT]

---

### Post by eawedat on 2010-03-19
Chesamo
1)I believe that there is something called PREFIX :) [ubuntu]
2)why do i have to do sudo while am logged as a root ?

---

### Post by Chesamo on 2010-03-19
> **eawedat said:**
> 1)I believe that there is something called PREFIX :) [ubuntu]
I was not aware that pico shipped with Ubuntu; I've never seen it used over nano or vi.
> **eawedat said:**
> 2)why do i have to do sudo while am logged as a root ?
Because Ubuntu disables the root account by default. You should not *ever* have to switch to root.

---

### Post by tgalati4 on 2010-03-19
man motd

---

### Post by uRock on 2010-03-20
> **tgalati4 said:**
> ```
man motd
```
+1 Manuals are great.

---

### Post by tgalati4 on 2010-03-20
tgalati4@tpad-Gloria7 ~ $ apropos motd
motd (5)             - message of the day
motd+shell (1)       - Print the message of the day and launch a shell
motd.tail (5)        - Template for building the system message of the day
pam_motd (8)         - Display the motd file
update-motd (1)      - Automatically update the message-of-the-day (MOTD)

---

### Post by zong1 on 2010-06-21
Ubuntu, for some reason, rewrites the /etc/motd each time it boots from some other file. I have no idea where. Its braindead.

---

### Post by styfle on 2011-09-23
> **zong1 said:**
> Ubuntu, for some reason, rewrites the /etc/motd each time it boots from some other file. I have no idea where. Its braindead.

According to the man page, "The contents of this   file   are  regenerated  upon  every  system  boot  based  on  the  contents  of /etc/motd.tail."

> MOTD(5)                            Linux Programmer’s Manual                           MOTD(5)

NAME
       motd - message of the day

DESCRIPTION
       The  contents  of /etc/motd are displayed by login(1) after a successful login but just
       before it executes the login shell.

       The abbreviation "motd" stands for "message of the day", and this file has been  tradi&#8208;
       tionally  used  for  exactly  that  (it  requires much less disk space than mail to all
       users).

       On Debian GNU/Linux this file is a symbolic link pointing to /var/run.  The contents of
       this   file   are  regenerated  upon  every  system  boot  based  on  the  contents  of
       /etc/motd.tail.

FILES
       /etc/motd
       /etc/motd.tail

SEE ALSO
       login(1), motd.tail(5), issue(5)

COLOPHON
       This page is part of release 2.77 of the Linux man-pages project.  A description of the
       project,  and  information  about  reporting  bugs,  can  be  found  at [http://www.ker&#8208;](http://www.ker&#8208;)
       nel.org/doc/man-pages/.

Linux                                     1992-12-29                                   MOTD(5)
 Manual page motd(5) line 1/34 (END)



---

