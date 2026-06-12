---
title: "not able to change permissions of owner"
date: 2012-07-16
forum: General Help
---

### Post by mahajan on 2012-07-16
~$ sudo chown -R root:dm/var/www/evernote1
sudo: must be setuid root
dm@ubuntu:~$ chown root:dm  /etc/sudoers
chown: changing ownership of `/etc/sudoers': Operation not permitted
dm@ubuntu:~$ chmod 440 /etc/sudoers
chmod: changing permissions of `/etc/sudoers': Operation not permitted

I want to change permission as owner root and my username is dm 
 but not able to access any files or folder with sudo
 i want to install oath-php but giving error 
must be setuid root  


please resolve this problem:confused:

---

### Post by NikTh on 2012-07-16
Hi  , 
hmm.. this seems like a sudo problem.. 
open a terminal and give this command 
```

ls -l $(which sudo)
``` post the results back here . 
Thanks

---

### Post by dino99 on 2012-07-16
sudoers is root:root and does not have to be changed

[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by techvish81 on 2012-07-16
try "gksu nautilus" to change permissions from "properties" in 
nautilus.
 the owner cannot be changed but you can get read/write permissions for user.

---

### Post by mahajan on 2012-07-16
> **NikTh said:**
> Hi  , 
hmm.. this seems like a sudo problem.. 
open a terminal and give this command 
```

ls -l $(which sudo)
``` post the results back here . 
Thanks

-rwxrwxrwx 2 root root 156824 2012-05-16 10:53 /usr/bin/sudo

---

### Post by mahajan on 2012-07-16
> **techvish81 said:**
> try "gksu nautilus" to change permissions from "properties" in 
nautilus.
 the owner cannot be changed but you can get read/write permissions for user.

dm@ubuntu:~$ gksu nautilus

(gksu:27755): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksu:27755): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksu:27755): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksu:27755): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",


and it is saying you are not the owner so you cannot change these permissions

---

### Post by mahajan on 2012-07-16
Go to recovery console (reboot, and chose recovery console in case you didn't catch on to how to do that),

fire following commands .


Code:
chown root:root /usr/bin/sudo
chmod 4755 /usr/bin/sudo
and reboot the machine by

Code:
shutdown -r now


In case if you are getting a "Sudo: /etc/sudoers is mode 0777, should be 0440" message on startup then

go to recovery console and fire following command

Code:
chmod 0440 /etc/sudoers

---

### Post by claracc on 2012-07-16
You are going to mess your filesystem, ownership of /etc/sudoers has to be root:root.

Read: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by NikTh on 2012-07-16
> **mahajan said:**
> -rwxrwxrwx 2 root root 156824 2012-05-16 10:53 /usr/bin/sudo
Hi, 
Your sudo is messed up .. follow @mahajan's suggestion about recovery mode
or else..
..prepare for new installation. 
Thanks

---

### Post by mahajan on 2012-07-24
dm@ubuntu:~$ ls -l $(which sudo)
-rwsr-xr-x 2 root root 156824 2012-05-16 10:53 /usr/bin/sudo

---

