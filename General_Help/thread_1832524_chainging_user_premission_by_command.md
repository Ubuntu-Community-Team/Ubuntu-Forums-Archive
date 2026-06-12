---
title: "chainging user premission by command??"
date: 2011-08-24
forum: General Help
---

### Post by ashu. on 2011-08-24
**[FONT=Comic Sans MS]HI [/FONT]**[FONT=Comic Sans MS]i hav been experimenting with my machine for quite  some time but came accross this problem recently [/FONT]to change user permission i used to use the command [SIZE=4]***users-admin***[/SIZE]

recetly when i tried to use it in root it wouldn't work it jus keeps loading n never really responds n process becomes a zombie..so can someone tell me an alternate way(preferably command) to change user permissions...plz plz help....

---

### Post by LowSky on 2011-08-24
enabling the root user can drastically effect your software experience. we do not recoomend it.  you should never use root to log into Ubuntu


Arch linux wiki has a great write up on how to add a user by command line
[https://wiki.archlinux.org/index.php/Beginners%27_Guide#Adding_a_User](https://wiki.archlinux.org/index.php/Beginners%27_Guide#Adding_a_User)

---

### Post by ashu. on 2011-08-24
> **LowSky said:**
> enabling the root user can drastically effect your software experience. we do not recoomend it.  you should never use root to log into Ubuntu


Arch linux wiki has a great write up on how to add a user by command line
[https://wiki.archlinux.org/index.php/Beginners%27_Guide#Adding_a_User](https://wiki.archlinux.org/index.php/Beginners%27_Guide#Adding_a_User)

thanks for the way 2 add user but wat i really needed to do was edit user permission via terminal.like addding a already existing (non sudo)user to admin group or removing permissions of a administrator(non root) account.i'd prefer commands so that i could show my friends the unix way of changing or somewhat near to it...

---

### Post by Habitual on 2011-08-24
[http://man.cx/adduser(8](http://man.cx/adduser(8))

you also modify existing users with adduser. ;)

---

### Post by fdrake on 2011-08-24
```

# add username to admin group
sudo addgroup username admin  
# how to remove username from admin group
sudo vim /etc/group
#delete the name of the user from the group
#ie. from admin:x:119:john:mary  to   admin:x:119:mary 

```

---

### Post by sisco311 on 2011-08-25
COMMANDS:
**useradd** - low level utility for adding users
**groupadd** - create group
**usermod** - modify a user account
**groupmod** - modify a group definition on the system
**adduser, addgroup** - On Debian or Ubuntu they are front ends to the low level tools like useradd, groupadd and usermod
**userdel** - delete a user account and related files
**groupdel** - delete a group
**deluser, delgroup** - On Debian or Ubuntu they are front ends to the low level tools like userdel and groupdel
**gpasswd** - administer /etc/group and /etc/gshadow
**passwd** - change user password
**chfn** - change real user name and information
**chsh** - change login shell
**vipw, vigr** - edit the password, group, shadow-password or shadow-group file

FILES:
/etc/passwd - the password file (see: **man 5 passwd**)
/etc/shadow - the shadowed password file (see: **man 5 shadow**)
/etc/group - group file (see: **man 5 group**)
/etc/gshadow - the shadowed group file (see: **man 5 gshadow**)

---

