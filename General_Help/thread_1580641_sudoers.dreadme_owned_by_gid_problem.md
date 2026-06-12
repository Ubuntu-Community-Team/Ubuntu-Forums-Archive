---
title: "sudoers.d/readme owned by gid problem"
date: 2010-09-23
forum: General Help
---

### Post by kdbrown5 on 2010-09-23
Hi, I'm on 10.10 beta I've run into a problem with sudo permissions.  I tried to mount another ext4 partition while following a tutorial and somehow mucked up some permissions with chown and chmod. 

Now when I try to sudo under my username, i get 
```
sudo: /etc/sudoers.d/README is owned by gid 1000, should be 0
>>> /etc/sudoers: /etc/sudoers.d/README near line 23 <<<
sudo: parse error in /etc/sudoers near line 23
sudo: no valid sudoers sources found, quitting
```

Also if i try su - I get authentication error.

I've tried fixes like chown -R root /etc/
chown -R username:username /etc/

and a few others but nothing seems to fix this.  
If anyone can help it would be greatly appreciated, I'm hesitant to reinstall as I have a few games set up in WINE with alot of modifications

---

### Post by silbak04 on 2010-09-23
read me your output for:

```

$ cat /etc/sudoers

```

---

### Post by kdbrown5 on 2010-09-23
> Defaults env_reset
# Host alias specification
# User alias specification
# Cmnd alias specification
# User privilege specification
root ALL=(ALL) ALL

# Allow members of group sudo to execute any command after they have provided their password
(Note that later entries override this, so you might need to move it further down)

%sudo ALL=(ALL) ALL
#
#includedir /etc/sudoers.d

#Members of the admin group may gain root priveleges
%admin ALL=(ALL) ALL

Also I viewed my sudoers.d/README and besides the disclaimer/info in the readme it showed

```
includedir /etc/sudoers.d
```

---

### Post by kdbrown5 on 2010-09-23
Not sure if this helps at all, 

[IMG]http://img823.imageshack.us/img823/8811/imag00552.jpg[/IMG]

---

### Post by kdbrown5 on 2010-09-24
Going to fix problem by reinstalling 

/endthread

---

### Post by mahajan on 2012-07-16
> **kdbrown5 said:**
> Also I viewed my sudoers.d/README and besides the disclaimer/info in the readme it showed

```
includedir /etc/sudoers.d
```

cat: /etc/sudoers: Permission denied
  how to resolve it

---

### Post by drs305 on 2012-07-16
> **mahajan said:**
> cat: /etc/sudoers: Permission denied
  how to resolve it

Since it's owned by root, you can't view it as a normal user:
[/CODE]```
sudo cat /etc/sudoers
```
But if you were trying to view the README, as mentioned in the earlier post it would be:
```
sudo cat /etc/sudoers.d/README
```

Since this thread is very old, it's now closed. If you have further questions please open your own thread. Happy Ubuntu-ing.

---

