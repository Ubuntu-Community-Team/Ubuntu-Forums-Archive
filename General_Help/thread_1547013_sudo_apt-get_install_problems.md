---
title: "sudo apt-get install problems"
date: 2010-08-06
forum: General Help
---

### Post by davidcookson145 on 2010-08-06
Hi

Recently got a VPS and installed Ubuntu Server[B] 9 (32bit)

When i go to install basic pages like php my admin with commands like..[/B]

sudo apt-get install phpmyadmin

I get a error like this:

root@PkNGssbkpT:/# sudo apt-get install phpmyadmin                              Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  phpmyadmin: Depends: php5-mcrypt but it is not going to be installed
              Depends: dbconfig-common but it is not going to be installed
              Depends: libjs-mootools but it is not going to be installed
              Recommends: php5-gd but it is not going to be installed
  webmin: Depends: libnet-ssleay-perl but it is not going to be installed
          Depends: libauthen-pam-perl but it is not going to be installed
          Depends: libio-pty-perl but it is not going to be installed
          Depends: libmd5-perl but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


I was wondering whats causing this and if i can fix this? as i do need phpmyadmin

Thanks

---

### Post by 3rdalbum on 2010-08-06
Did you try what it suggests, which is running:

```
sudo apt-get install -f
```

---

