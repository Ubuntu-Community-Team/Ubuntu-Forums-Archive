---
title: "User account and general settings"
date: 2011-09-16
forum: General Help
---

### Post by victorsanchezuk on 2011-09-16
Hi all,

I am new to Linux, very new to Linux. I have installed ubuntu 11.04 64bits on a USB and it works great!

I am struggling with a couple of things:

-What is the best way to set up the user accounts? I will need administrator rights so I can download and install programs without pop up windows all the time. Also eventually run some c++ programs.

-I am currently under live session user and all the settings and programs disappear every time I turn the computer off.

I probably haven't used the right terminology but hopefully you understand.

Thanks in advance,

Victor

---

### Post by raja.genupula on 2011-09-16
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

this is for keeping your ubuntu changes in USB .

& 

you said you're a new guy to ubuntu so some basic commands here for you 
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

all the best .

---

### Post by t0p on 2011-09-16
The account set up when installing Ubuntu *is* an administrator account.  It is normal for Ubuntu to as for a password when you want to do something that requires administrative permissions for a couple of reasons:

- the password request gives you a chance to think again whether you really want to do it (sometimes you can screw your computer if you do something as "root" (ie admin) incorrectly;

- if you've left your computer unattended for a few moments and a malicious person comes along, he might want to do something to harm your computer.  If he doesn't know your password, he will be unable to do anything bad that requires admin privileges.

There are other distros (and different OSes) that have more liberal admin policies.  If these password "pop-ups" really bother you that much, perhaps a migration may be in order?

---

### Post by haqking on 2011-09-16
For administration privelege Canonical (Ubuntu) supports the use of [SUDO]("https://help.ubuntu.com/community/RootSudo") for temporary elevated privelege.  To carry out a admin task then :

for CLI based apps
```

sudo <command>
```and for graphical apps

```
gksudo <command>
```Please make sure you read this [ROOTSUDO]("https://help.ubuntu.com/community/RootSudo") to understand why it is used, how to use it and why it is a bad idea to remove the pop up authentication requests you mentioned.

The password required when it asks you is YOUR OWN PASSWORD, [B]do not enable to the root account or log in as root

[/B]To setup user accounts see [here]("https://help.ubuntu.com/10.04/serverguide/C/user-management.html")

---

### Post by Wim Sturkenboom on 2011-09-16
> **t0p said:**
> ...
- if you've left your computer unattended for a few moments and a malicious person comes along, he might want to do something to harm your computer.  If he doesn't know your password, he will be unable to do anything bad that requires admin privileges.
Sorry, but that is totally incorrect and gives a false sense of security. Reboot,recovery mode; do I have to continue with the rest how to become root without even being asked for a password? Not to mention that one can start a graphical environment as root from there?

> **t0p said:**
> 
There are other distros (and different OSes) that have more liberal admin policies.  If these password "pop-ups" really bother you that much, perhaps a migration may be in order?
At least some of those have (or used to have) the decency to ask for a root password when entering single user mode ;) Even modifying grub while booting requires a password. Wonder what is more secure ;)

---

### Post by haqking on 2011-09-16
> **Wim Sturkenboom said:**
> Sorry, but that is totally incorrect and gives a false sense of security. Reboot,recovery mode; do I have to continue with the rest how to become root without even being asked for a password? Not to mention that one can start a graphical environment as root from there?


At least some of those have (or used to have) the decency to ask for a root password when entering single user mode ;) Even modifying grub while booting requires a password. Wonder what is more secure ;)

+1

Physical access always has been and always will be Root access though !

---

### Post by Wim Sturkenboom on 2011-09-16
> **haqking said:**
> +1

Physicaly access always has been and always will be Root access though !I know. However Ubuntu makes it easy to do it quickly.

---

