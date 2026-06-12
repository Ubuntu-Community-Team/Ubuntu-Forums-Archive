---
title: "Super User help"
date: 2010-12-02
forum: General Help
---

### Post by MaxTakeoff on 2010-12-02
Hi, I finally managed to get Xubuntu installed on my old laptop (Toshiba Satellite 1.7GHz P4) - it has a very dodgy and fussy DVD drive, I ended up burning the CD image to a DVD but that´s another story!

Anyway I have been using various Linux distributions for quite some years but have always had a root account and done administrative tasks by doing su - while logged in as a regular user.
So when I installed Xubuntu, I didn´t realize that the methodology was different so my initial user was set up as stu.  The problem is that I wanted my wife and kids to use this account and not be able to do any damage, so when I realized that all they had to do to access super user programs was to type stu´s password, I made another account (admin) and gave that administrator rights with a different password and made stu into a regular user.

Now my issue is that I used to be able to do things like mount another partition, while logged in as stu, copy files, change the owner and then stu could immediately access them.  It seems that with Ubuntu, I need to log stu out, log in as admin, mount the partition and copy the files, then log admin out and log stu back in?  Surely there must be an easier way?  Is there a way to set up stu so that when he issues a sudo command, he needs admin´s password and not his own?

---

### Post by surfer on 2010-12-02
the user you installed the system with is equipped with admin rights. but su is no longer used to get root rights. you have to either use
```
$ sudo command
```
in order to execute 'command' with root privileges, or you can start a root shell with
```
$ sudo -s
```
the password is always your user password.

---

### Post by surfer on 2010-12-02
sorry, i misread your post...

you can always su into your admin account
```
$ su admin
```
and sudo stuff from there. on the command line that is...

---

### Post by MaxTakeoff on 2010-12-02
That´s it!!!  Exactly what I needed, thanks surfer!!  And thanks for the fast response, sweet!!

---

