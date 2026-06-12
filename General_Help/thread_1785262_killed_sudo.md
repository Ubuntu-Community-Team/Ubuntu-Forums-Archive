---
title: "killed sudo"
date: 2011-06-18
forum: General Help
---

### Post by evilbrent on 2011-06-18
Whilst trying to repair permissions on a recalcitrant portable hard drive I accidentally ran 
```

sudo chown brent -R *cd /
```which apparently changes ownership of all the files ending in cd to brent. I'm presuming that wasn't the only stupid thing I did, but I've screwed up the permissions pretty bad is was I'm saying.

Now I can't use sudo. (Also have no sound manager, no switch-user, and portable-drive situation has deteriorated, but one thing at a time.) 

I've had a suggestion to run **[COLOR=#2D2411][FONT=arial, helvetica, sans-serif]sudo apt-get --reinstall install `dpkg --get-selections | grep install | grep -v deinstall | cut -f1`[/FONT][/COLOR]** which restores permissions apparently, but I can't use **sudo** at all. Even **sudo cd /** gives "sudo: must be setuid root"

The output of** ls -l /usr/bin/sudo** is ```
-rwxr-xr-x 2 brent root 127668 2011-01-20 05:01 /usr/bin/sudo
``` Shouldn't this be root,root?

I've tried:
[B]chown root:root /usr/bin/sudo
chmod 4755 /usr/bin/sudo[/B]

but just get told that I don't have permission to do it.

Can anyone help me get root access so I can try to fix the permissions so that I can try to make linux accept that my hard drive is actually a read-write filesystem?

---

### Post by blazemore on 2011-06-18
Root access is easy to come by.

On the Grub menu, before Ubuntu boots, edit the kernel line to add the following
```
init=/bin/bash
```

Then boot with Ctrl+X

Voila! Instant root!

---

### Post by jarrah-95 on 2011-06-18
simmilarly to above, if you run the first command you tried (im not sure personally about it, but it may work) as root. if you boot into recovery mode (at grub) then just choose root terminal and your all good. 
just a side note, * is a linux wild card, meaning it means anything quite useful in searches, but could be dangerous (eg when used with rm -rf) but you probably know that now :D

---

### Post by evilbrent on 2011-06-18
> **blazemore said:**
> Root access is easy to come by.

On the Grub menu, before Ubuntu boots, edit the kernel line to add the following
```
init=/bin/bash
```Then boot with Ctrl+X

Voila! Instant root!

Ok so I just tried that twice and I'm not root. I still don't have permission to change anything.

---

### Post by evilbrent on 2011-06-18
> **jarrah-95 said:**
> simmilarly to above, if you run the first command you tried (im not sure personally about it, but it may work) as root. if you boot into recovery mode (at grub) then just choose root terminal and your all good. 
just a side note, * is a linux wild card, meaning it means anything quite useful in searches, but could be dangerous (eg when used with rm -rf) but you probably know that now :D

Ok Jarrah - I tried this with reasonable success. I was able to get a root prompt and carry out my chown and chmod on /usr/bin/sudo. Unfortunately now sudo just says

```
brent@Bertha:~$ sudo
sudo: /etc/sudoers.d/README is owned by uid 1000, should be 0
>>> /etc/sudoers: /etc/sudoers.d/README near line 24 <<<
sudo: parse error in /etc/sudoers near line 24
sudo: no valid sudoers sources found, quitting
```

---

### Post by evilbrent on 2011-06-18
DOUBLE FIST PUMP IN THE AIR!!!!!!!!!!!!!!  (really)

Jarrah you may have saved my marriage!

I'll finish my report for those who may follow:

Booting into root through grub gave me root access. Then I was able to change the ownership of /usr/bin/sudo. 

That brought its own problems: "etc/sudoers.d/README is owned by uid 1000, should be 0"

which I googled and then used the grub root shell to type

chown root:root /etc/sudoers 
chmod 440 /etc/sudoers
chown -R root:root /etc/sudoers.d
chmod  755 /etc/sudoers.d 
chmod  440 /etc/sudoers.d/*

and now I have root again!!

---

