---
title: "Too many password authorizations"
date: 2010-11-23
forum: General Help
---

### Post by Randymanme on 2010-11-23
This isn't just an Ubuntu complaint -- PCLinuxOS is guilty too.  I'm pretty tired of  having to type in my password for anything little thing.  How can I  disable password authorization dialog boxes except for more important  stuff like package management?  Linux Mint does have a 15 minute grace  period so that you don't have to retype your password after having done  it once.

---

### Post by clhsharky on 2010-11-23
Randymanme

> Linux Mint does have a 15 minute grace period so that you don't have to retype your password after having done it once. 
Ubuntu is same by default, thats where Mint got it. All my buntu installs are same with 15 min grace. Your permission config may have been changed, can happen when system is run in root, or configured improperly. I'm not sure how to correct yours, but have seen on this forum before.

Hope this helps
FilePermissions - Community Ubuntu Documentation
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)


Sharky

---

### Post by Randymanme on 2011-11-14
As far as I can tell, so far, Oneiric doesn't have the 15 minute grace.  How can I enable it?

Any advice would be  appreciated.  Thanks. 
[B]
[/B]

---

### Post by BillyBoa on 2011-11-14
There is no solution to this annoyance. Even in the new LinuxMint 12 I installed, I don't have this 15min grace. 

Only solution to install the application Parcellite from the Center just to be able to keep copied things to the clipboard and copy and paste your password to the dialogue box.

---

### Post by oldos2er on 2011-11-14
"sudo" timeout is controlled by the /etc/sudoers file. Edit it with the command ```
sudo visudo
```

[https://help.ubuntu.com/community/RootSudoTimeout](https://help.ubuntu.com/community/RootSudoTimeout)

---

### Post by haqking on 2011-11-14
> **BillyBoa said:**
> **There is no solution to this annoyance.** Even in the new LinuxMint 12 I installed, I don't have this 15min grace. 

Only solution to install the application Parcellite from the Center just to be able to keep copied things to the clipboard and copy and paste your password to the dialogue box.

Just edit the sudo timeout.

[https://help.ubuntu.com/community/RootSudoTimeout](https://help.ubuntu.com/community/RootSudoTimeout)

And people keep complaining about passwords, usually the same people who complain about getting their box pwn3d.

Security exists for a reason in a networked world.

edit: ninja'd above by oldos2er ;-)

---

