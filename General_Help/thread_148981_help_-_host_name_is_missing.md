---
title: "help - host name is missing"
date: 2006-03-23
forum: General Help
---

### Post by lunatic on 2006-03-23
Hi, today after reboot there was a problem while logging in followig message appeared I'm a n00b please help me out

**"Could not lookup internet address for (none) This will prevent GNOME from operating correctly. It may be possible to correct the problem by adding (none) to the /et/hosts"**

And below that two options are displayed "login anyway" or "try again" 
My host name is changed to "(none)", because of this im not able to use some administrative stuff. Can any one help me out!

---

### Post by paulipe on 2006-03-23
try editting the file /etc/hostname
my computer name is paulipe so create an entry paulipe in the file below.
```
sudo nano /etc/hostname

```

the first line of /etc/hosts should look something like this
```
127.0.0.1 localhost.localdomain localhost paulipe.whatever.domain.com paulipe
```

Hope that helps. Otherwise try going to "System->Administration->Networking" and see what settings you can change there

---

### Post by lunatic on 2006-03-23
still the probelm exists plz any one can suggest me some thing else. My host name is zionmainframe and now ti turned out to be (none) this is the /etc/hosts file and I can't open up System > Adminstration > Networking as the host name is changed to (none)

> 127.0.0.1 localhost.localdomain localhost zionmainframe
172.16.16.150 zionmainframe

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


---

### Post by dcstar on 2006-03-23
[QUOTE=lunatic]still the probelm exists plz any one can suggest me some thing else. My host name is zionmainframe and now ti turned out to be (none) this is the /etc/hosts file and I can't open up System > Adminstration > Networking as the host name is changed to (none)[/QUOTE]
Try the "hostname" command and see what it says.

---

### Post by lunatic on 2006-03-23
I've tried 
echo $HOSTNAME 
and it showed nothing
then i tried 
echo $(hostname) 
it showed "(none)"
still the problem is there help me im a n00b :confused:

---

### Post by dcstar on 2006-03-23
[QUOTE=lunatic]I've tried 
echo $HOSTNAME 
and it showed nothing
then i tried 
echo $(hostname) 
it showed "(none)"
still the problem is there help me im a n00b :confused:[/QUOTE]
The "hostname" command is "hostname", please try it.

---

### Post by ZylGadis on 2006-03-23
He did that actually. echo $(hostname) has the same effect. Obviously the hostname is indeed (none).

lunatic, again, make sure that your /etc/hostname file contains a single word, zionmainframe in your case. Here is mine:

```

alex@woof:~$ cat /etc/hostname
woof
alex@woof:~$

```

I would do something like

```

sudo echo zionmainframe > /etc/hostname

```

That should take care of it.

---

### Post by lunatic on 2006-03-24
> cat /etc/hostname 
zionmainframe
its already there still the problem exists any other way?

---

### Post by dcstar on 2006-03-24
[QUOTE=ZylGadis]He did that actually. echo $(hostname) has the same effect. Obviously the hostname is indeed (none).
.......[/QUOTE]
It is **not** the same, using the hostname command uses the gethostname() function, and when it is run any error message can indicate where a potential problem may be.

Good luck with finding a solution.

---

