---
title: "SU Authentication Failure"
date: 2010-02-19
forum: General Help
---

### Post by aravel on 2010-02-19
Hi everyone,

I have installed Ubuntu 8.04 inside windows and every time I go to the terminal and type "su" it asks me for a password.  Well the password I set before the install doesn't work, it gives me an authentication failure.  I thought that since it was inside windows it didn't set me as a root user.  I go to user groups and I see my name there and then "root" above it, but its grayed out.  Is there a default root password I can enter?  Any help with this would be great!  Thanks!

---

### Post by akakingess on 2010-02-19
I take it you running Ubuntu within Windows? I haven't done that myself, but I would say that usually you should just run one command at a time, for instance "sudo gedit /etc/fstab" to edit the fstab file as root, but your password should work as long as you were the one to install it or are in the admin and/or root group. Sorry I couldn't be of more assistance and let us know if even that works.

---

### Post by sisco311 on 2010-02-19
By default, the root account password is locked in Ubuntu. This means that you cannot login as root directly or use the su command to become the root user. However, since the root account physically exists it is still possible to run programs with root-level privileges. This is where sudo comes in - it allows authorized users (normally "Administrative" users) to run certain programs as root without having to know the root password.
[uhelp]community/RootSudo[/uhelp]

---

### Post by akakingess on 2010-02-19
> **sisco311 said:**
> By default, the root account password is locked in Ubuntu. This means that you cannot login as root directly or use the su command to become the root user. However, since the root account physically exists it is still possible to run programs with root-level privileges. This is where sudo comes in - it allows authorized users (normally "Administrative" users) to run certain programs as root without having to know the root password.
[uhelp]community/RootSudo[/uhelp]

Thanks for clarifying sisco311, I really didn't know if the protocol for running it within Windows was the same as standalone, but I definitely try to steer anyone away from the "commands" that we should not even discuss on the forums ;)

---

### Post by diegoful on 2010-07-18
If you really have to, try:

```
sudo su
```

;)

---

### Post by TheBrewmaster on 2010-08-21
I'm having a similar problem, under lucid.  I changed my password a week ago, and now certain things won't work due to getting an authentication error.  What's odd is, I can log in, I can change my password, and sudo works fine.  My user is in the admin group.  However, su won't authenticate, and neither will installing software from the Ubuntu Software Center.
I just tried the suggestion of doing:
```
sudo su
```
and that worked.  
I'm thinking that somehow I messed something up when I changed my password, I used passwd, but something, I think it was my keyrings password still wasn't synced, and I edited a file that I can't remember what (I know, dumb move to not document what he changes for someone who doesn't really know what he's doing), and I no longer had the problem of having to type in my old password to unlock my keyrings.  Using the old password won't authenticate for su or the Ubuntu Software Center either.

So far, haven't quite seen anything that's the same as my problem that was actually solved, unfortunately.

---

