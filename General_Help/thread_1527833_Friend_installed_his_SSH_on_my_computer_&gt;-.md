---
title: "Friend installed his SSH on my computer &gt;:-/"
date: 2010-07-09
forum: General Help
---

### Post by falven on 2010-07-09
How do I remove him? he cleaned up after himself pretty well, he even cleared my terminal history...

---

### Post by matey3 on 2010-07-09
do you mean he used your username or your root to get in?

or do you mean he can ssh into your system without login in?

have you changed your passwords yet?
there are ways to disable passwordless login via ssh

---

### Post by falven on 2010-07-09
> **matey3 said:**
> do you mean he used your username or your root to get in?

or do you mean he can ssh into your system without login in?

have you changed your passwords yet?
there are ways to disable passwordless login via ssh

How do I disable passwordless login?
He somehow added his SSH key to my system, I saw him login once...

---

### Post by hansdown on 2010-07-09
Hi falven.

Click system> administration> login screen.

Unlock it with your password, and click "show the screen for who will login".

---

### Post by falven on 2010-07-09
> **hansdown said:**
> Hi falven.

Click system> administration> login screen.

Unlock it with your password, and click "show the screen for who will login".

Done, what will this do?

---

### Post by Zip247 on 2010-07-09
Have you looked at you auth.log to see if someone has ssh'ed in

a quick way to check if he has.

From the command line

```
cat /var/log/auth.log | grep sshd
```

---

### Post by hansdown on 2010-07-09
> **falven said:**
> Done, what will this do?

It will require a login by you, the user, and your password.

Some things you need to check, in case some settings have been changed;

1: Click system> preferences> personal file sharing.

Be sure the settings are like the first screenshot.

2: click system> preferences> remote desktop.

Be sure the settings are like the second screenshot.

!!! The rule of thumb, is if you think your system has been "HAD", then do a fresh install. with strong passwords. !!!

---

### Post by Zip247 on 2010-07-09
you could also check to see if his public key is stored on your authorized_keys2 file of your .ssh directory

```
cat /home/[COLOR="Red"]user[/COLOR]/.ssh/authorized_keys2
```

where [COLOR="Red"]user[/COLOR] is your user name

and if it is, remove it from the file

---

### Post by falven on 2010-07-09
> **Zip247 said:**
> you could also check to see if his public key is stored on your authorized_keys2 file of your .ssh directory

```
cat /home/[COLOR=Red]user[/COLOR]/.ssh/authorized_keys2
```where [COLOR=Red]user[/COLOR] is your user name

and if it is, remove it from the file

What if he removed it...

---

### Post by Zip247 on 2010-07-10
> **falven said:**
> What if he removed it...

Then he is not using ssh keys to log into your machine.

---

### Post by falven on 2010-07-10
ssh [email]---@---.---.com[/email]
Found him :) Muahaha

---

### Post by Zip247 on 2010-07-10
if he is getting in with ssh and not using keys, you need to change your user password.

---

### Post by d3v1150m471c on 2010-07-10
Firstoff, change your password.

if you don't use ssh or telnet then **turn them off. **otherwise:
```

sudo iptables -A INPUT -i eth0 -p tcp --dport 22 -m state --state NEW -m recent --set --name SSH
sudo iptables -A INPUT -i eth0 -p tcp --dport 22 -m state --state NEW -m recent --update --seconds 300 --hitcount 3 --rttl --name SSH -j DROP

```That will allow only 3 ssh connection attempts every 5 minutes in the event someone is using a dictionary attack on your machine. note: those rules won't stay intact after you logout so you'll need to append those commands to /ect/init.d/rc.local. change "eth0" in the code to the appropriate service.

---

