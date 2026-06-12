---
title: "Preventing another hack attempt"
date: 2010-08-27
forum: General Help
---

### Post by Monotoko on 2010-08-27
Hi there,

One of my servers has recently been attacked, it has one remote SSH user which cannot run 'sudo'

However, someone managed to gain the password to that account on the server then used "vi /etc/passwd" to gain a list of users, then launched a bruteforce using su against my admin account.
(that's what I can gather from the logs)

This did not get very far before I saw and kicked the user off and changed all of the passwords, but I would like to know how to prevent this sort of thing happening again.

I need to know mainly how to stop the SSH user running su in the first place and how to stop the user seeing files like /etc/passwd

Anyone have any suggestions?

Daniel

---

### Post by AlphaLexman on 2010-08-27
You need to set up 'ssh' to use 'authorized keys' on both/all machines.
[http://www.eng.cam.ac.uk/help/jpmg/ssh/authorized_keys_howto.html](http://www.eng.cam.ac.uk/help/jpmg/ssh/authorized_keys_howto.html)

---

### Post by Monotoko on 2010-08-27
I have reason to suspect that it was someone I previously gave the password to that did the hack attempt, so this would still have happened.

What I am mainly after is a way to ensure this user cannot use su?

Daniel

---

### Post by AlphaLexman on 2010-08-27
Change the password.

---

### Post by geirha on 2010-08-27
Install [john the ripper](apt:john) and let it bruteforce all passwords in the background. If any passwords are found within a month, block the account(s).

If you want a secure password, make it at least 12 character long and make sure it has at least one uppercase letter, one lowercase letter and at least one digit or other characters. You won't manage to bruteforce such a password in this lifetime with today's computers.

---

