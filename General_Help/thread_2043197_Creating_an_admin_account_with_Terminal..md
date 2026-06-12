---
title: "Creating an admin account with Terminal."
date: 2012-08-16
forum: General Help
---

### Post by melrokz on 2012-08-16
How do I create an 'administrator' account on Ubuntu 12.04 using the command line? Does this convert an ordinary user to an 'administrator' user with all privileges?

```

sudo adduser melvin
sudo adduser melvin admin

```

If not, please let me know the right commands. Thanks in advance.

EDIT: Got it.
```

sudo adduser melvin
sudo adduser melvin sudo

```

That worked for me. Thanks to auronandace :)

---

### Post by melrokz on 2012-08-16
Please, may I have an update on this?

---

### Post by smartboyhw on 2012-08-16
Mate, there's no admin now, we use only sudo in 12.04.

---

### Post by melrokz on 2012-08-16
No, a standard user gets a message saying that he is not in the sudoers file and that the incident will be reported???

```


reshmi@melvin-pc:~$ sudo apt-get update
[sudo] password for reshmi: 
reshmi is not in the sudoers file.  This incident will be reported.

```

---

### Post by Lars Noodén on 2012-08-16
You can use [gpasswd](http://manpages.ubuntu.com/manpages/precise/en/man1/gpasswd.1.html) to add your user to a group.

```

sudo gpasswd --add melvin sudo
sudo gpasswd --add melvin adm

```

---

