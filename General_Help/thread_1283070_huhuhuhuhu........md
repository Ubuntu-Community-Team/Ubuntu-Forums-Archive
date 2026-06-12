---
title: "huhuhuhuhu......."
date: 2009-10-05
forum: General Help
---

### Post by meluzi02 on 2009-10-05
I accidentally removed the smb.conf file from etc folder...

is there any possible solution to recover that?

---

### Post by renkinjutsu on 2009-10-05
i did some searching, and it doesn't seem like any of the smb packages contain a .conf file in the /etc directory.. So it's probably generated after installation when the daemon boots up.

Try just rebooting and see what happens
if that doesn't work, then.
```
sudo aptitude reinstall smbclient samba-common
```

---

### Post by skillllllz on 2009-10-05
It's as simple as this ```
sudo dpkg-reconfigure samba-common
```

---

### Post by moster on 2009-10-05
I could sent you mine ;)

---

### Post by meluzi02 on 2009-10-05
tnx for your reply 

i got this result:

[B]marvz@MARVZ:~$ sudo dpkg-reconfigure samba-common
[sudo] password for marvz: 
/usr/sbin/dpkg-reconfigure: samba-common is broken or not fully installed[/B]

---

### Post by skillllllz on 2009-10-05
> **meluzi02 said:**
> tnx for your reply 

i got this result:

[B]marvz@MARVZ:~$ sudo dpkg-reconfigure samba-common
[sudo] password for marvz: 
/usr/sbin/dpkg-reconfigure: samba-common is broken or not fully installed[/B]

hmm... 

try:

```
sudo touch /etc/smb.conf
sudo dpkg-reconfigure samba-common
```

---

### Post by ad_267 on 2009-10-05
Try this too and see what you get:

```
sudo dpkg --configure -a
```

---

