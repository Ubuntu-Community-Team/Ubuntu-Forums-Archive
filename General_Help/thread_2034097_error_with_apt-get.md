---
title: "error with apt-get"
date: 2012-07-27
forum: General Help
---

### Post by whitesferry on 2012-07-27
when running apt-get upgrade i get the following error

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en 
Fetched 20.1 MB in 9s (2,185 kB/s)                                                                                                         
Error org.freedesktop.DBus.Error.Spawn.ExecFailed: Cannot launch daemon, file not found or permissions invalid
Reading package lists... Done

---

### Post by lisati on 2012-07-27
Are you using sudo? e.g.
```

sudo apt-get upgrade

```

---

### Post by whitesferry on 2012-07-27
indeed!

---

### Post by claracc on 2012-07-28
In the third line: Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en, the link point to a security notice and not to software packages.

So I would comment the line with [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en in /etc/apt/sources.list

---

### Post by whitesferry on 2012-07-28
i've tinkered with the file a bit and it seems that the last entry that is uncommented always throws the error.

I have gone to another workstation and scp'd a known good sources file and i still get the same error over and over

i did an 
apt-get -f install
apt-get autoremove (there were a ton of apps in the commmand above, and it said i should run it )


thanks for any continued help i can get

---

### Post by claracc on 2012-07-29
I should edit sources.list:

In terminal run command, sudo gedit /etc/apt/sources.list (you will have to enter your root password), and go to the line containing [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en, comment it typing # symbol before the line, close and save file and try to upgrade again

---

