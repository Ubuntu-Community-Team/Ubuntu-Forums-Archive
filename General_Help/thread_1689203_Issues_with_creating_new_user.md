---
title: "Issues with creating new user"
date: 2011-02-16
forum: General Help
---

### Post by LanguidLegend on 2011-02-16
I am on my own laptop, running Ubuntu 10.10, and before this, I only had my one username (adam).
```
adam:~$ sudo su
root:/home/adam# useradd -d /home/achoate -s /bin/bash achoate
root:/home/adam# ls /home
adam
root:/home/adam# usermod -p password achoate
root:/home/adam# tail -1 /etc/shadow
achoate:password:15021:0:99999:7:::
root:/home/adam# tail -1 /etc/passwd
achoate:x:1001:1001::/home/achoate:/bin/bash
root:/home/adam# ls -a /home
.  ..  adam
root:/home/adam# su achoate
achoate:/home/adam$ exit
exit
root:/home/adam# exit
exit
adam:~$ sudo su achoate
achoate:/home/adam$ 
```
So, as you can see, I'm having issues 1)creating a /home/achoate directory, 2)setting it as the default for user achoate, and 3)setting a password (shouldn't it have prompted me?)


Also, once this is settled, can you tell me if there is a way to automically login as root (or give one of the users root-privileges)? It's annoying to have to constantly re-enter my root password for su commands..

Thanks in advance!!

---

### Post by quixote on 2011-02-17
```
sudo -i
```will log you in as root in a terminal until you ```
exit
```back to your own user. If you want a regular graphical login for root, it is possible to assign a separate password to root.  If that's really what you want, I'll try to dig up the old link that goes through the steps. 

I'm no expert on the useradd command, so this is just a suggestion.  Why not start simple and just let the system put in its defaults. I.e.:```
#useradd achoate
```Once the user has been created you can (still as root) type ```
#passwd achoate
```and it lets you "change" the password.  Unix (and linux) consider no password to some password a change. :)

---

