---
title: "Password not accepted"
date: 2011-05-03
forum: General Help
---

### Post by Alan.Brown on 2011-05-03
Hi Peepl

I am running Ubuntu 11.04 which I like very much (except for Unity - so I am using Ubuntu Classic).

Whenever I try to use "**su - **" I get Password Authentication Failure.    I have checked Caps Lock (obviously) and have also tried resetting the password using "**passwd**" - but with no success.

If I use "**sudo ....**" with a command the password is accepted.

I have the same software installed on two computers but the problem only occurs on one - the other is OK!!!

Any suggestions??

TIA

Alan

---

### Post by idoitprone on 2011-05-03
```
sudo su
```to enter root


root is disable in Ubuntu on default so typing su which requires the root pass wont work
sudo on the other hand uses the user pass not the root which works

btw, you dont need to enter root
sudo is sufficient for your needs.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Alan.Brown on 2011-05-03
Thanks for your reply.  It solves my problem.

I am curious as to why it works OK one one computer and not the other.

Alan

---

