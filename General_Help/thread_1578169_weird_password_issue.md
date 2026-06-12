---
title: "weird password issue"
date: 2010-09-20
forum: General Help
---

### Post by onesojourner on 2010-09-20
I am having a weird issue with my ubuntu password. I have my desktop set to auto log me in. It does and then it asks for the default keyring and I type that and all is fine, unless I switch users or I try to use my password to install updates ect. Does any one have any idea what could be going on?

---

### Post by nothingspecial on 2010-09-20
> **onesojourner said:**
> I am having a weird issue with my ubuntu password. I have my desktop set to auto log me in. It does and then it asks for the default keyring and I type that and all is fine, unless I switch users or I try to use my password to install updates ect. Does any one have any idea what could be going on?

I think you need to elaborate a bit.

What happens when you try to use your password to install stuff or switch users?

---

### Post by onesojourner on 2010-09-21
When update manager pops up, the little box pops up that says reading packages like normal and then it just goes back to the update manager and doesn't do anything else. I can repeat this over and over and nothign else happens. When I try to do it from terminal:

```
peter@desktop:~$ sudo apt-get update
[sudo] password for peter: 
Sorry, try again.
[sudo] password for peter: 

```

---

### Post by nothingspecial on 2010-09-21
Ubuntu is not recognising your password for whatever reason.

Reboot and hold down shift key to enter the grub menu

Choose root recovery shell or whatever they call it nowadays.

Once in that type 

```
passwd peter
```

It will then ask you for a new password, you`ll have to type it twice. You can ignore all that stuff about phone numbers etc (you`ll see what I mean)

Then type ```
exit
``` and boot as normal.

---

### Post by CharlesA on 2010-09-21
It sounds like you changed the password outside of the Users and Passwords area. They will cause it to not be in sync with the keyring.

---

### Post by onesojourner on 2010-09-22
That got it. Thank you.

> **nothingspecial said:**
> Ubuntu is not recognising your password for whatever reason.

Reboot and hold down shift key to enter the grub menu

Choose root recovery shell or whatever they call it nowadays.

Once in that type 

```
passwd peter
```

It will then ask you for a new password, you`ll have to type it twice. You can ignore all that stuff about phone numbers etc (you`ll see what I mean)

Then type ```
exit
``` and boot as normal.

---

### Post by nothingspecial on 2010-09-22
> **onesojourner said:**
> That got it. Thank you.

Glad you got it sorted :)

---

