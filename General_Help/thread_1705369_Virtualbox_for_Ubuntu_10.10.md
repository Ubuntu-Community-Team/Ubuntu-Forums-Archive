---
title: "Virtualbox for Ubuntu 10.10"
date: 2011-03-12
forum: General Help
---

### Post by kloakenratte on 2011-03-12
Hi! I have installed VirtualBox on my Ubuntu. Then I created with the wizard a Win XP VM. When I try to start this VM for the first time, I get this error:

Failed to load VMMR0.r0 (VERR_SUPLIB_OWNER_NOT_ROOT). 
Unknown error creating VM (VERR_SUBLIB_OWNER_NOT_ROOT). 

Errorcode: NS_ERROR_FAILURE (0x0004005) 
Component: Console
Interface: IConsole {515e8e8d-f932-4d8e-9f32-79a52aead882}

Thank you for your help!

Sandy

---

### Post by kloakenratte on 2011-03-12
nobody any idea?

---

### Post by M4570D0N on 2011-03-12
possible solutions:

[http://www.virtualbox.org/ticket/7889](http://www.virtualbox.org/ticket/7889)
[http://forums.virtualbox.org/viewtopic.php?f=8&t=37448](http://forums.virtualbox.org/viewtopic.php?f=8&t=37448)

It looks like it may be an issue with permissions settings with one of several possible directories, or possibly multiple directories, not being owned by "root." Check your log files and see if there are any VB related error messages and look for any lines that mention a folder/directory as not being owned by root.

Possible examples:

'/usr' directory owner is not "root"
```
pdmR3LoadR0U: pszName="VMMR0.r0" rc=VERR_SUPLIB_OWNER_NOT_ROOT szErr="The owner is not root: '/usr'"
```
'/opt' directory owner is not "root"
```
pdmR3LoadR0U: pszName="VMMR0.r0" rc=VERR_SUPLIB_OWNER_NOT_ROOT szErr="The owner is not root: '/opt'"
```

Change the owner of any directories you see listed to "root"

---

### Post by kloakenratte on 2011-03-13
the owner of "/opt" is "root". 
the owner of "/usr" is "sandy", my user. do i have to change the owner of /usr, because when i try it, i get a message, that i am not allowed to change the owner of this directory. 
is this the problem?

---

### Post by M4570D0N on 2011-03-21
> **kloakenratte said:**
> the owner of "/opt" is "root". 
the owner of "/usr" is "sandy", my user. do i have to change the owner of /usr, because when i try it, i get a message, that i am not allowed to change the owner of this directory. 
is this the problem?

Sorry for the late reply, but yes, change the owner of the "/usr" directory to root.

Open the terminal and enter this:
```
$ sudo chown -R root:root /usr
```
then reboot.

If for some reason that does not work, try rebooting into recovery mode, then entering:
```
chown -R root:root /usr
```
then reboot.

---

