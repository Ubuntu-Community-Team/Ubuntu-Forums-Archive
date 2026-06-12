---
title: "ssh client suddenly started to ask me for passphrase for all my servers (keys exists)"
date: 2011-08-18
forum: General Help
---

### Post by yamagami on 2011-08-18
All of the sudden whenever I ssh into any of my servers the ssh clients asks me for my rsa key passphrase (which does not exist), and when I press enter, it continues to ask for the remote server's account password. All of my public/private keys were working fine allowing me passwordless login to my servers until now.

[PHP]
harel@mylaptop:~/.ssh$ ssh myserver
Enter passphrase for key '/home/harel/.ssh/id_rsa': <<< There is no passphrase, and key looks ok
harel@spiderman's password: <<< why start now?
[/PHP]

Any idea what can cause that?

Thanks, 

Harel

---

### Post by Habitual on 2011-08-18
in terminal:
```

ls -al /home/harel/.ssh/id_rsa
```

is it 600 (-rw-------) ?

---

### Post by yamagami on 2011-08-18
Yes! but I'm not sure what it should be. Tried the following and up and this is what I get...

Permissions 0640 for '/home/harel/.ssh/id_rsa' are too open.
It is recommended that your private key files are NOT accessible by others.
This private key will be ignored.

---

### Post by Habitual on 2011-08-18
Terminal >
```
chmod 600 /home/harel/.ssh/id_rsa
```

All ssh key files in ~/.ssh should be 600

---

### Post by yamagami on 2011-08-18
But they are at 600... I also tried now to make all the files there 600 and still the same problem - keeps asking for passphrase followed by the password to any server that used to work yesterday without any passwords.

---

### Post by fdrake on 2011-08-18
> **yamagami said:**
> Yes! but I'm not sure what it should be. Tried the following and up and this is what I get...

Permissions 0640 for '/home/harel/.ssh/id_rsa' are too open.
It is recommended that your private key files are NOT accessible by others.
This private key will be ignored.

check your config file

```
less /etc/ssh/ssh_config
```

from man ssh_config

```

 BatchMode
    40               If set to “yes”, passphrase/password querying will be disabled.  In addition, the ServerAliveInterval
    41               option will be set to 300 seconds by default.  This option is useful in scripts and other batch jobs where
    42               no user is present to supply the password, and where it is desirable to detect a broken network swiftly.
    43               The argument must be “yes” or “no”.  The default is “no”.


```

---

### Post by yamagami on 2011-08-19
Thanks fdrake, that worked. I don't know why this behaviour changed all of the sudden. Maybe one of the latest updates from canonical...

---

### Post by yamagami on 2011-08-19
It appears that with that setting set to yes, It won't let me ssh  into servers that actually do require me to log in (to which I don't have a key..) 
This is very odd! I don't get how this behaviour just appears...

---

### Post by fdrake on 2011-08-19
> **yamagami said:**
> It appears that with that setting set to yes, It won't let me ssh  into servers that actually do require me to log in (to which I don't have a key..) 
This is very odd! I don't get how this behaviour just appears...

i don't know .... i never used this kind of option myself.

ps. if your problem is solved mark it as "solved", as reference future users

---

### Post by yamagami on 2011-08-19
Nope. not solved yet, nor do I know how it started. 
I'm afraid my only option is to try to regenerate my keys on all servers....

EDIT: seems to be resolved.... I am really not sure how or what of the suggestions above did the trick but its ok... so closing this one.

---

