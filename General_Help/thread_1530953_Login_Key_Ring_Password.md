---
title: "Login Key Ring Password?"
date: 2010-07-14
forum: General Help
---

### Post by jereece on 2010-07-14
I just installed Ubuntu on a new computer.  When I set it up I told it to login automatically and I verified that setting is still in place.  All of a sudden today I start getting prompted to enter a password for the login key ring?  I was not getting this prompt and I have the setting in System>Admin>Login Screen set to automatically log in.  What happened and what do I need to do to fix this annoying problem.

Thanks,
Jim

---

### Post by jward3010 on 2010-07-14
This is different from login. The key ring is a little program that saves and encrypts your passwords inside the session, things like wireless keys, 802.1x security etc. It's a little overkill in my view but it's used in Ubuntu. I'm not sure how to kill it or disable it. But, understand - it IS different from logging into your user account, it's a second stage of security.

---

### Post by jereece on 2010-07-14
I am using wireless on this computer but the popup sure does sound like a login issue.  It says;

> Enter password for your login key.  Your login keyring did not get unlocked when you logged into your computer.

Plus I have been using this for days without getting this prompt. Wonder why it just all of a sudden started?

If anyone has a solution I would appreciate the help.

Jim

---

### Post by philinux on 2010-07-14
> **jereece said:**
> I just installed Ubuntu on a new computer.  When I set it up I told it to login automatically and I verified that setting is still in place.  All of a sudden today I start getting prompted to enter a password for the login key ring?  I was not getting this prompt and I have the setting in System>Admin>Login Screen set to automatically log in.  What happened and what do I need to do to fix this annoying problem.

Thanks,
Jim

[http://maketecheasier.com/auto-unlock-keyring-manager-in-ubuntu-intrepid/2009/03/14](http://maketecheasier.com/auto-unlock-keyring-manager-in-ubuntu-intrepid/2009/03/14)

---

### Post by K.J. on 2010-07-14
> **philinux said:**
> [http://maketecheasier.com/auto-unlock-keyring-manager-in-ubuntu-intrepid/2009/03/14](http://maketecheasier.com/auto-unlock-keyring-manager-in-ubuntu-intrepid/2009/03/14)

Be advised that this solution will store your password UNENCRYPTED. Use at your own risk.

---

### Post by jereece on 2010-07-17
That worked for logging in now I get the same prompt when I launch Evolution.  This is getting frustrating.  Why am I having Key Ring problems with a fresh install?

Thanks for any help.

Jim

---

### Post by derwiki on 2010-07-19
I'm getting a problem where it keeps prompting me when I'm trying to ssh using a passphrase with a key. This only started happening after I rebooted and there are no security updates waiting to install. Would any other information help?

---

### Post by jward3010 on 2010-07-19
> **jereece said:**
> That worked for logging in now I get the same prompt when I launch Evolution.  This is getting frustrating.  Why am I having Key Ring problems with a fresh install?

Thanks for any help.

Jim
It has nothing to do with the fresh install, the keyring is latched into a few programs where high sensitivity information is located - passwords, wireless keys, e-mails and account information. Unfortunately disabling it if you want less security is a cumbersome situation. It will probably be linked in with IM software as well like Pidgin or Gwibber - anything that stores your personal passwords and information.

---

### Post by jereece on 2010-07-19
What would happen if I deleted the key ring in .gnome2\keyrings?

---

