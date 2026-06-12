---
title: "login root (debian with su, ubuntu with sudo)"
date: 2004-10-22
forum: General Help
---

### Post by sp on 2004-10-22
Hello

I have used debian sid and now use ubuntu, but an aspect of ubunty don¨t undestand, the use of sudo, whit deiban I had a account of root activate, l read the advantages from sudo but I don,t convince.

[http://wiki.ubuntu.com/RootSudo#head-bac1c04472f484ad6650fa6bf4c8f3b33f14b217](http://wiki.ubuntu.com/RootSudo#head-bac1c04472f484ad6650fa6bf4c8f3b33f14b217)

What happens if a malicious user hacks the user account to us, he will have permissions whit sudo?

Excuse me form my bad english, l from spain

---

### Post by golem3 on 2007-03-06
Copying and pasting from the link you posted

"Every cracker trying to brute-force their way into your box will know it has an account named root and will try that first. What they don't know is what the usernames of your other users are."

So you are much safer using "sudo" over "su root." Hope that helps.

---

### Post by melancholeric on 2007-03-06
"Every cracker trying to brute-force their way into your box will know it has an account named root and will try that first. What they don't know is what the usernames of your other users are."

a/ if it's a remote login, root login can be disabled (and usually is). So, the attacker would first have to login as regular user and then su to root. So which is safer?

b/ if it's local it doesn't matter in the slightest: he could hit the power button and reboot to single user mode. Or just steal the hard drive.

sudo might be safer in some ways, but definitely not because of that.

---

