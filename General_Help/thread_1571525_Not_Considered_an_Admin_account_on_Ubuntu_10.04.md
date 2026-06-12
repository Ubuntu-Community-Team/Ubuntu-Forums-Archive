---
title: "Not Considered an Admin account on Ubuntu 10.04?"
date: 2010-09-09
forum: General Help
---

### Post by weasker on 2010-09-09
I have installed ubuntu 10.04 on my desktop. After taking a networking class last semester in college i decided to try out some of the linux commands and things i learned. When i try to change permissions of a folder using chmod 7777 [folder name], i get a message saying denied because i do not have permission to do that. When installing the OS, i don't recall making an admin account but just made a user and don't recall selecting if it is an admin account or not. Any help would be appreciated! Also how do i make it so that a folder needs a password to open it?

---

### Post by andrewthomas on 2010-09-09
any command that requires admin permissions needs to be prefaced with sudo

ex
```
sudo command
```
and it will ask you for your user password

---

### Post by bodhi.zazen on 2010-09-09
See also 

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by weasker on 2010-09-09
Is there a way to make it so ubuntu doesn't require me to type sudo? basically make that user absolute admin?

---

### Post by egalvan on 2010-09-09
> **weasker said:**
> Is there a way to make it so ubuntu doesn't require me to type sudo? basically make that user absolute admin?

Yes there is, but if you have to ask how, then you should not do it.

See bodhi.zazen post above...
please folow the link, and read the page, and try to udnerstand it.
The Linux security model is the main reason for Linux being so secure.

---

### Post by NearlyALaugh on 2010-09-09
Being root at all times is a **very bad idea**. See the documentation:

[https://help.ubuntu.com/community/RootSudo#Enabling%20the%20root%20account](https://help.ubuntu.com/community/RootSudo#Enabling%20the%20root%20account)


When you're playing around with shell commands, just stay in your home directory and change permissions and mess around there. No sudo required. Changing the settings of root folders can harm your system.

---

### Post by bodhi.zazen on 2010-09-09
> **weasker said:**
> Is there a way to make it so ubuntu doesn't require me to type sudo? basically make that user absolute admin?

Yes , but we do not support that here and it is a bad idea. Running as a non-privilaged account for daily tasks is an essential part of security.

You can use

```
sudo -i
```for a root shell and 

```
gksu nautilus --no-desktop
``` for a graphical interface.

You can also configure sudo so that it does not ask for a password.

---

