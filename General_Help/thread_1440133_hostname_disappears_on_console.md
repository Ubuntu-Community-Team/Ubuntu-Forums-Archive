---
title: "hostname disappears on console"
date: 2010-03-27
forum: General Help
---

### Post by satimis on 2010-03-27
Hi folks,

Ubuntu 9.10 64bit

On console:- 

login as root
root@aaa:~#

login as userA
$

hostname disappears

$ cat /etc/hostname```

aaa

```


$ cat /etc/hosts```

127.0.0.1	aaa.localhost		aaa
127;0.1.1	aaa
192.168.0.204	aaa.satimis.com		aaa

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```


Also tried;
$ cat /etc/hosts```

127.0.0.1	localhost
127;0.1.1	aaa
192.168.0.204	aaa.satimis.com		aaa
.....

```


Please advise how to fix the problem.


Ran;
# useradd -m userA

to create userA


B.R.
satimis

---

### Post by gmargo on 2010-03-27
Either it's the typo in your hosts file (semicolon in aaa's 127 IP address), but that can't be it if root works, or your PS1 variable is not set.  Try setting PS1 to
```

PS1='\u@\h \!\$ '

```Hostname should show up in the \h field.

---

### Post by satimis on 2010-03-27
> **gmargo said:**
> Either it's the typo in your hosts file (semicolon in aaa's 127 IP address), but that can't be it if root works, or your PS1 variable is not set.  Try setting PS1 to
```

PS1='\u@\h \!\$ '

```Hostname should show up in the \h field.

Hi gmargo,

Sorry I don't follow

Whether run;```

PS1='\u@\h \!\$ '

```

on console as root, replacing \h with\hostname ?

I doubt whether following command on creating user is correct?  Particularly the option "-m"```

$ sudo useradd -m userA

```


Previously I also ran;```

$ sudo userdel -r userB

```

Any influence.  Thanks


B.R.
satimis

---

### Post by dimoftheyard on 2010-03-27
You should run the command in the console, but not as root, but as the user whose prompt is wrong. It sets the variable PS1, which determines what the prompt looks like. 

I think it is more interesting which shell you are using. It looks very much like sh which isn't a good idea. You can find that out be executing
```
echo $SHELL 
```
You could try
```
usermod -s `which bash` userA 
```
to change the login shell of userA to bash, which is the default in Ubuntu. That of course only works if bash is installed, but it should be on any Ubuntu system.

---

### Post by satimis on 2010-03-27
> **dimoftheyard said:**
> You should run the command in the console, but not as root, but as the user whose prompt is wrong. It sets the variable PS1, which determines what the prompt looks like. 


Hi dimoftheyard,

Wheter to login userA (it has problem with wrong prompt).  Then run on console```

PS1='\u@\h \!\$ '

```
h=hostname


> 
I think it is more interesting which shell you are using. It looks very much like sh which isn't a good idea. You can find that out be executing
```
echo $SHELL 
```


$ echo $SHELL```

/bin/sh

```

> 
You could try
```
usermod -s `which bash` userA 
```
to change the login shell of userA to bash, which is the default in Ubuntu. That of course only works if bash is installed, but it should be on any Ubuntu system.

$ usermod -s `which bash` userA```

usermod: cannot lock /etc/passwd; try again later.

```

Thanks

Edit:

$ usermod -s `which bash` root```
   
usermod: no changes

```

$ su -
Password: 
# usermod -s `which bash` root```

usermod: no changes

```

B.R.
satimis

---

### Post by dimoftheyard on 2010-03-29
Hi satimis,

the command to set PS1 was ment to be entered as is. \h is replaced by the hostname automaticly.
But that is only a temporary solution anyway, your shell is /bin/sh, that's the problem. I'm sorry I didn't write the correct command to change it, try
```
chsh -s /bin/bash userA
```
That should prompt you for your password and change the shell. This will not change the shell you are working in, but any newly started shell should be bash after that. At least after you logout and login again, but it should be working before that also.
In a non-bash shell you can also type
```
bash
```
to start bash.

Your root user already has bash, that's why usermod said "no changes".

Hope this helps

---

### Post by satimis on 2010-03-29
> **dimoftheyard said:**
> Hi satimis,

the command to set PS1 was ment to be entered as is. \h is replaced by the hostname automaticly.
But that is only a temporary solution anyway, your shell is /bin/sh, that's the problem. I'm sorry I didn't write the correct command to change it, try
```
chsh -s /bin/bash userA
```
That should prompt you for your password and change the shell. This will not change the shell you are working in, but any newly started shell should be bash after that. At least after you logout and login again, but it should be working before that also.
In a non-bash shell you can also type
```
bash
```
to start bash.

Your root user already has bash, that's why usermod said "no changes".


Hi dimoftheyard,

Thanks for your advice.

Problem already solved as follow;

$ sudo userdel -r userA

$ sudo adduser userA


B.R.
satimis

---

