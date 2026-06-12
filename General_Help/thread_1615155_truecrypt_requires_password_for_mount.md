---
title: "truecrypt requires password for mount"
date: 2010-11-06
forum: General Help
---

### Post by CTBuckweed on 2010-11-06
I use truecrypt to encrypt a file containing my sensitive data (credit card numbers, bank account info, etc).

When I mount my encrypted file through truecrypt, I enter the password for my file. That's OK - I want to keep it that way. But when it gets mounted as a file system, ubuntu also requires that I enter the 'su' password.

How do I get around this?

I run ubuntu 10.04 (Lucid)

---

### Post by CharlesA on 2010-11-06
If you don't want to be prompted for the password when you use sudo mount, read [here]("https://help.ubuntu.com/community/RootSudo") and [here]("http://fedorasolved.org/post-install-solutions/sudo").

---

### Post by CTBuckweed on 2010-11-06
Well, perhaps I didn't fully explain... I double-click on the file (the truecrypt volume I wish to mount) and the truecrypt interactive application gets launched. After I enter the file's encryption password on the truecrypt application, not command line mode. Then I get a prompt asking me for the administrator's password (presumably to mount the truecrypt volume as a file system).

---

### Post by CharlesA on 2010-11-06
yeah, it's probably asking for yer password so that it can mount it.

Not quite sure how you can get around that, but maybe look at the sudoers file, since I know you can exclude a command from prompting for yer password, but I am not sure of the syntax.

---

### Post by alphaamanitin on 2010-11-06
I am not sure you can get around it, in a solution just for it.  I know you can make certain commands exempt from needing the sudo password.  I have read people who got tired of using sudo for apt-get update and apt-get upgrade, so I know you could get around it for a mount as well.  However, I am not sure you can make it not needed for just this particular TrueCrypt volume.  

One of the books I have read, I think Ubuntu Hacks, or possibly Ubuntu Tool-Kit, describe how to get around the sudo neet for apt-get commands.  I think it was one of those books.  It might have been a tutorial on linuxcommando though.

AlphaA

---

