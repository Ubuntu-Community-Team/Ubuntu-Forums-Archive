---
title: "Koha - MySQL conflict"
date: 2010-08-24
forum: General Help
---

### Post by tomdag on 2010-08-24
I've been trying to install koha version 3.00.04_fixed onto ubuntu 10.04 as per the instructions at [http://www.botskool.com/programming-tutorials/linux/installing-koha-ubuntu-904-910-1004](http://www.botskool.com/programming-tutorials/linux/installing-koha-ubuntu-904-910-1004).  The installation goes fine until step 12. I cannot finish (using option 2) as it requires a file and a folder named koha-zebraqueue-daemon in the same directory. Neither of these existed before and it is impossible to create both as you cannot have a folder and file that share the same name. 

Also, when trying to log on to 127.0.1.1 koha spits out these errors:
[SIZE=3]The following fatal error has occurred:[/SIZE]
                          Access denied for user 'root'@'localhost' (using password: YES) at /usr/share/koha/lib/C4/Context.pm line 666.
Compilation failed in require at /usr/share/koha/lib/C4/Auth.pm line 30.
BEGIN failed--compilation aborted at /usr/share/koha/lib/C4/Auth.pm line 30.
Compilation failed in require at /usr/share/koha/opac/cgi-bin/opac/opac-main.pl line 22.
BEGIN failed--compilation aborted at /usr/share/koha/opac/cgi-bin/opac/opac-main.pl line 22.

[FONT=Arial]Any help would be appreciated.[/FONT]

---

