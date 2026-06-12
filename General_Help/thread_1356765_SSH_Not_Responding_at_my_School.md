---
title: "SSH Not Responding at my School"
date: 2009-12-16
forum: General Help
---

### Post by Mimz on 2009-12-16
My friend and I are trying to SSH connect to my ubuntu computer at home but for some reason at my school when we try to connect using the ssh command it won't do anything.

It will stall for a good 3 or 4 minutes and then say it can't connect

What would be a reason for this problem?

---

### Post by whiteychs on 2009-12-16
School might have the default SSH port (22) blocked.

---

### Post by doas777 on 2009-12-16
you can find out if the port is accessible with telnet (at the terminal)

```
 telnet <targetIP> 22
```
if your port is accessible, it will provide a command prompt like this. just use ctrl+c to close it.
```
Trying 10.x.y.z...
Connected to 10.x.y.z.
Escape character is '^]'.


```

if your port is not accessible (or the admin is blocking TCP/23) it will hang while connecting and display an error message.

---

### Post by earthpigg on 2009-12-16
if port 22 turns out to be blocked, you could always switch to a different port. ssh works the same on any port, 22 is just the 'normal' one used.

ssh -p 5555 user@123.123.123.123

change /etc/ssh/sshd_config on your ubuntu computer to use port 5555 (or whatever you pick) and restart it for changes to take effect.

also, make sure it is allowed by school rules, bla bla, before you do this. (we all know teenagers dont care about rules, but it had to be said.)

---

### Post by prem1er on 2009-12-16
> **earthpigg said:**
> if port 22 turns out to be blocked, you could always switch to a different port. ssh works the same on any port, 22 is just the 'normal' one used.

ssh -p 5555 user@123.123.123.123

change /etc/ssh/sshd_config on your ubuntu computer to use port 5555 (or whatever you pick) and restart it for changes to take effect.

also, make sure it is allowed by school rules, bla bla, before you do this. (we all know teenagers dont care about rules, but it had to be said.)

+1 use port 443, as it is more likely to be opened.

---

### Post by Dark_Stang on 2009-12-16
Or any random port over 1024.

---

### Post by doas777 on 2009-12-16
> **prem1er said:**
> +1 use port 443, as it is more likely to be opened.
and encrypted no less, so the protocol analyzers in the IDPS won't raise a ruckus either.

---

### Post by Mimz on 2009-12-16
how do I modify the sshd_config file? I modified something and it said that I don't have the right permissions...

---

### Post by prem1er on 2009-12-16
```
sudo vi /etc/ssh/sshd_config
```

---

### Post by earthpigg on 2009-12-16
> **prem1er said:**
> ```
sudo vi /etc/ssh/sshd_config
```

nano is easier to use.

```
sudo nano /etc/ssh/sshd_config
```

or gedit...

```
sudo gedit /etc/ssh/sshd_config
```

you get the idea, pick your text editor :D

this is the line you want to change:

```
Port 22
```

change it to any 4 or 5 digit number you can easily remember. remember that this stuff is case sensitive. make sure that word stays "Port" and not "port".

---

### Post by doas777 on 2009-12-16
> **prem1er said:**
> ```
sudo vi /etc/ssh/sshd_config
```

you may want to try this instead if you are in a desktop environment:
```
gksu gedit /etc/ssh/sshd_config
```
vi can be a real pain for those who don't want to spend forever learning it's eccentricities.
esc + ':' + 'wq' is not a good way to save a file.

---

### Post by Mimz on 2009-12-16
Thanks I'll post if it worked or not when I get home

---

### Post by earthpigg on 2009-12-16
here is a decent writeup on ssh:

[http://wiki.archlinux.org/index.php/SSH](http://wiki.archlinux.org/index.php/SSH)

yeah, its from arch, but its also a simple and well written guide.

skip these two sections, as they do not apply to ubuntu:
-Installing OpenSSH 
-Managing SSHD Daemon 

the rest is exactly the same. works the same on any linux distro, and im pretty sure its the same stuff on OS X too (yes, you can ssh to/from a Mac just as well/easily).

---

### Post by StuartN on 2009-12-16
You could always use ssh over http, e.g. [http://www.linuxquestions.org/questions/linux-server-73/setting-up-http-over-ssh-595280/](http://www.linuxquestions.org/questions/linux-server-73/setting-up-http-over-ssh-595280/) - your network administrator might help you with the settings, or even unblock the specific port you require.

---

