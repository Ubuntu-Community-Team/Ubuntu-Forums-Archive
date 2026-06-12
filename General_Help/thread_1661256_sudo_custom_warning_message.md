---
title: "sudo custom warning message"
date: 2011-01-06
forum: General Help
---

### Post by darc26 on 2011-01-06
Hello Everyone!

I was thinking there should be a way of generating a custom message if someone tries to execute a sudo command in a certain directory and maybe even on a specific file.  I'm fairly new to linux and ubuntu and I feel like this should be possible.

Thanks for any help.

-Dave

---

### Post by artie_effim on 2011-01-06
hate to do this to you, but you'll have to change the file /etc/sudoers.  And you'll have to read `man sudoers` - but I don't know if you have the granular control that way (dir and file).  Happy hunting.

---

### Post by bodhi.zazen on 2011-01-06
> **darc26 said:**
> Hello Everyone!

I was thinking there should be a way of generating a custom message if someone tries to execute a sudo command in a certain directory and maybe even on a specific file.  I'm fairly new to linux and ubuntu and I feel like this should be possible.

Thanks for any help.

-Dave

You will almost certainly need to write a wrapper for sudo to do this.

---

