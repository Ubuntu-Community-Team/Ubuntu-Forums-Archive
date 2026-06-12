---
title: "User Permissions?"
date: 2011-11-28
forum: General Help
---

### Post by hantechbl on 2011-11-28
I'm writing a basic script, basically a main user should be able to su into other user's accounts, this is a better way of organizing processes than the previous method I had, but how would I create a user, set a password, and then make it so lets say user: bob can access all "sub-accounts"?  (It would be nice if I was able to do this within a bash script, I know how to make a user and a password, but not without being interactive, is there a way to do this non-interactively?

---

### Post by Synoc on 2011-11-28
So you want "Bob" to be able to access every account created AFTER him? if I read this right?
or do you you want any account created after to be accessible to any account created before?

---

### Post by hantechbl on 2011-11-28
That is correct, I'd like it if he were able to simply su into users without inputting a password.

---

### Post by Synoc on 2011-11-28
only an admin or someone with full sudo privileges can access all accounts. if "Bob" is in that category a simple 

```
 sudo bash 
``` would mean he'd never need another password. in UBUNTU Linux. but there is a security risk in saying Bob can su into any account created afterwards. 

the main problem being a lack of Accountability. I do recommend against this plan. can I ask why you need access like that?

---

### Post by Lars Noodén on 2011-11-29
Synoc's suggestion is a step in the right direction.  You can refine the sudo permissions in [/etc/sudoers](http://manpages.ubuntu.com/manpages/precise/en/man5/sudoers.5.html).  It's possible to allow just su to specific accounts:

```

%bobsgroup  ALL = (ALL) NOPASSWD: /bin/su acct1, /bin/su acct2, /bin/su acct3

```

You'll have to list the accounts individually unless there is a regular expression that will match them and only them.

---

### Post by Synoc on 2011-11-29
thanks, I had (and have) no idea how to edit the sudoers file. Is there some good documentation on how do to that?

---

### Post by Lars Noodén on 2011-11-29
Not really.  Sudo is one of the more underutilized/underappreciated tools.  There is some Ubuntu Community Documentation:
[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

and I put together a presentation on Sudo which has some examples:
[http://www.bsdly.net/~lars/Lectures/Network-06-sudo.odp](http://www.bsdly.net/~lars/Lectures/Network-06-sudo.odp)

---

