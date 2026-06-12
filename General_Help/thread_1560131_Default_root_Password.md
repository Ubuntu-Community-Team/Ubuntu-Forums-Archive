---
title: "Default root Password"
date: 2010-08-24
forum: General Help
---

### Post by jackbuntu-common on 2010-08-24
I just installed Ubuntu 10.04 on one of my desktops.  I tried logging in to the "root" account, but I don't know the password.  Is there a default password for that account?  Thanks in advance.

--Jack

---

### Post by lisati on 2010-08-24
In Ubuntu, the root account is disabled by default. The usual way of accessing admin privileges is with the "sudo" command. Have a look here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Chris1274 on 2010-08-24
You can change the root password to whatever you want:
```
sudo su passwd
```
Disclaimer: You should login as root rarely, if ever. Most functions requiring root privileges can be executed with the sudo command (although I find it helpful to have access to the root account in order to do fixes in recovery mode).

---

### Post by wasp.wasp on 2010-08-24
Thank you kindly.

---

### Post by lisati on 2010-08-24
> **wasp.wasp said:**
> I installed 1.04-1 yesterday and was never asked to set a root password, which I find disturbing, hence my follow-up and addition to the previous post. Obviously, I am unable to install any packages and would sincerely appreciate any thoughts and help on the matter.

Have a look at the information that has already been posted. The preferred method of accssing "root" privileges with Ubuntu is via the sudo command, which uses your normal password.

---

### Post by wasp.wasp on 2010-08-24
Actually, that command produced the error "Sorry, please try again." I suppose this is because I need root privileges to run the sudo command.

---

### Post by alphaamanitin on 2010-08-24
> **wasp.wasp said:**
> Actually, that command produced the error "Sorry, please try again." I suppose this is because I need root privileges to run the sudo command.

This is odd.  It should ask you for a password.  Can you explain in more detail?

AlphaA

---

### Post by Chris1274 on 2010-08-24
That is strange. You should only need your normal user account password, and then  it should say, "Enter new UNIX password:" and then ask you to retype it.

---

### Post by cdenley on 2010-08-24
You should not set a root password. It is safer to have no valid root password, which is the default. Recovery mode should work without requiring a password when no root password is set. I think you should be able to do anything as root using sudo without setting a root password.

You obviously don't need root privileges to run the "sudo" command, since that is the only way to gain root privileges on an ubuntu system. You should only need an admin account, and YOUR password (not root's). I'm pretty sure this would have been explained in the link provided.

---

