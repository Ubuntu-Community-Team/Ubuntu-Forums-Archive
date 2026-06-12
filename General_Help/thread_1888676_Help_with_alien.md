---
title: "Help with alien"
date: 2011-11-29
forum: General Help
---

### Post by Onisutra on 2011-11-29
Hello, forum.

I need help converting a RPM in to a DEB. I have only been able to find people talking about alien. Well alien does not work for me and I have tried almost everything. The error I get from this is..

error: incorrect format: unknown tag
Warning: Skipping conversion of scripts in package MySQL-server: postinst preinst prerm
Warning: Use the --scripts parameter to include the scripts.
chown: cannot access `MySQL-server-5.6.3_m6//etc/my.cnf': No such file or directory
failed chowning /etc/my.cnf to 0:0: Illegal seek at /usr/share/perl5/Alien/Package/Rpm.pm line 265, <GETPERMS> line 3.

and I have been unable to resolve it. I have been told that alien may not work on a 64 bit system because of the way it was designed. If anyone can assist me or tell me of another program that would allow me to convert RPM in to a DEB.. that would be great.

Thank you for your time,
Oni

p.s.
I am using Ubuntu 10.04, and have no plans on updating. Gnome 3 is horrific. =\

---

### Post by llamabr on 2011-11-29
I don't know about 64 bit, but a 32 bit program should run on your 64 bit machine.  So don't just tell us the error, also tell us what command you typed.

---

### Post by Mark Phelps on 2011-11-30
My experience in using alien was that it was very hit-and-miss, meaning, some would convert, others would not.  

You would do much better either searching for a .deb package, or downloading the source and building the executable.

---

