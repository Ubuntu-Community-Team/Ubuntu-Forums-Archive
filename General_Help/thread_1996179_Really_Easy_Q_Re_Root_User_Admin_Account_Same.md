---
title: "Really Easy Q Re: Root User/ Admin Account Same?"
date: 2012-06-03
forum: General Help
---

### Post by Alcidious on 2012-06-03
Hi,

I'm running Ubuntu 11.10 32-bit. I've read over and over not to log in and run your system as root, but is this the same as the main user/admin account first set up during installation?  When I install programs I always use sudo ... but do I need to create an additional personal account to use for everyday email, browsing, etc? Or am I fine using the main account, given Ubuntu's protections against running as root?

Thanks, I know this is a really simple question... but I'm still a newbie. 

Alcidious

---

### Post by idoitprone on 2012-06-04
> **Alcidious said:**
> Hi,

I'm running Ubuntu 11.10 32-bit. I've read over and over not to log in and run your system as root, but is this the same as the main user/admin account first set up during installation?  When I install programs I always use sudo ... but do I need to create an additional personal account to use for everyday email, browsing, etc? Or am I fine using the main account, given Ubuntu's protections against running as root?

Thanks, I know this is a really simple question... but I'm still a newbie. 

Alcidious

nope not the same


root is an user in your system that controls everything
you cannot loggin as a root, but it is locked in ubuntu

sudo is a command that allows you to run commands as other users
for example.  run the command
```
whoami
```it should return your accound
but  I want to run a command as idoit

```
sudo -u idoit whoami
```it should return that I am an idoit

It could only run commands as proxy of users that exist on your system

the most likely case is the default which run commands as root

A sudoer is basically a user in the sudoers group that can run root
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by phaed on 2012-06-04
Root is separate from the main user account. You don't need to create another one.

---

### Post by Alcidious on 2012-06-04
Awesome! I really appreciate the clarification.  I'm getting ready to rid my pc of my windows partition, and I wanted to be sure I wasn't making a really stupid mistake (by using my usual account) ... thanks again!

---

