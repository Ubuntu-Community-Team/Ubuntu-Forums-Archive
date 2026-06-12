---
title: "SSH logins"
date: 2010-01-11
forum: General Help
---

### Post by residentevil on 2010-01-11
Hey!
I was wandering if there is a way to restrict ssh logins for a certain user only to one IP address. For example: the user **test **can login only from **some.random.ip.addresss**

Thanks in advance fellas :)

---

### Post by Tipo on 2010-01-11
Certainly :-)

You can make use of the /etc/hosts.allow file.

You can get the best information on this by running:

```
man hosts.allow
```

The gist of it is, you add this line to the /etc/hosts.deny file:

```
SSHD: ALL
```

And then add the IP you want to allow in the /etc/hosts.allow file:

```
SSHD: some.random.ip.address
```

This will deny ALL ssh logins, except those from that IP.

You can restrict access to certain users by editing the /etc/sshd_config file, as described here: [http://www.macosxhints.com/article.php?story=20031006145736131]("http://www.macosxhints.com/article.php?story=20031006145736131")

The link is for Mac OS X, but should apply to most *nix's

---

### Post by slakkie on 2010-01-11
There is no need for /etc/hosts.{allow,deny}. 

In /etc/ssh/sshd_config add the line:

```

AllowUsers user@ip.add.re.ss user@*.mydomain.com

```

```

AllowUsers
This keyword can be followed by a list of user name patterns,
separated by spaces. If specified, login is allowed only for
users names that match one of the patterns. `*' and `'? can be
used as wildcards in the patterns. Only user names are valid; a
numerical user ID is not recognized. By default, login is
allowed for all users. If the pattern takes the form USER@HOST
then USER and HOST are separately checked, restricting logins to
particular users from particular hosts

```

You can test it by running *sudo /usr/sbin/sshd -p 2048* and then login (*ssh -p 2048 user@server*) from the remote box with a user that is allowed access from all networks and one which isn't. If this works, you can kill sshd process:  *pkill -f "sshd -p 2048"*. Then restart your normal sshd process: */etc/init.d/ssh restart* (or use stop/start).

You can also use DenyUsers, which I do on my own laptop where my gf has an account, but with a weak password, I don't allow her ssh access at all. 

See man sshd_config for more options.

---

### Post by residentevil on 2010-01-12
10x, that worked just perfectly :)

---

