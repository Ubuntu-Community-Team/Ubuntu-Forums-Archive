---
title: "Shell script for ssh login"
date: 2011-10-24
forum: General Help
---

### Post by SACHINVD on 2011-10-24
Hi 
I am writing shell script for ssh login.

```

ssh_auth(){
(echo $pass) | ssh $user@$server
}

server="192.168.1.5"

# SSH User name
USR="root"
pass="password"

ssh_auth

```

after running above script I am getting error 
"Pseudo-terminal will not be allocated because stdin is not a terminal."

After running ssh command it ask for password.
To give password in script , pipelined password to ssh
```
 (echo $pass) | ssh $user@$server
```

Is there other way to provide password in script ?

Thanks !

---

### Post by tors on 2011-10-24
There is a program called "expect" which one could use.

#> sudo apt-get install expect


#> man expect
NAME
       expect - programmed dialogue with interactive programs, Version 5

...

---

### Post by SACHINVD on 2011-10-24
hi,

I tried to connect to remote unix machine using pexpect command in python script with correct login id and password, still i am getting error as permission denied.
My code is as follow:- 
```

#!/usr/bin/python2.4
import pexpect


# Create connection to a specific IP using 'admin' username
connector = pexpect.spawn('ssh root@10.77.65.17', timeout=5000)
connector.expect('.password:*')

print connector.before
print connector.after

# Enter password
connector.sendline('agent123')

```

I am getting error as follow.

python2.4 f.py
Permission denied, please try again.
Permission denied, please try again.
Permission denied (publickey
,password

any pointer on this. why script not sending correct password and giving wrong password?.

---

### Post by tors on 2011-10-24
Do you think the permission denied-message is local or remote?

Perhaps root-login is disabled on remote side?

---

### Post by mikejonesey on 2011-10-24
use a key...

---

### Post by Lars Noodén on 2011-10-24
As mikejonesey mentions, it is better to use a [key](http://www.debian-administration.org/articles/530).  The key can be with or without a password, better with a password.  Even if you do have a password for your key, if you use an [agent](http://mah.everybody.org/docs/ssh) you can cache the credentials and then only need to enter the password once even if you log in multiple times.

---

