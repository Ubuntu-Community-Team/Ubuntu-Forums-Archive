---
title: "Group questions."
date: 2010-09-29
forum: General Help
---

### Post by kyoji on 2010-09-29
Hi, I have just started to learn more about group management, and come across some things that have me stumped. 

First, I am unable to get group passwords to work at all in 10.4. I set the password for the group and try to `newgrp` in to it, the prompt asks for the password, but always gives me permission denied (even though its set to allow this.."\: x \:"). Is this just not fully supported? 

Next, after using `sudo gpasswd -A usr grp`, the user becomes an admin of the group, he can add/remove users only for that grp, but is not a "member". How would I find out who are admins of groups? I have tried `groups`, looking in /etc/group and theres nothing, the user does't even look like hes associated with the group at all.:confused:
 
I hope some one can clear this mystery up for me.

---

### Post by sisco311 on 2010-09-30
> **kyoji said:**
> Hi, I have just started to learn more about group management, and come across some things that have me stumped. 

First, I am unable to get group passwords to work at all in 10.4. I set the password for the group and try to `newgrp` in to it, the prompt asks for the password, but always gives me permission denied (even though its set to allow this.."\: x \:"). Is this just not fully supported? 


It's a known BUG, fixed in [shadow SVN]("http://svn.debian.org/wsvn/pkg-shadow"). 

From [http://svn.debian.org/wsvn/pkg-shadow/upstream/trunk/NEWS](http://svn.debian.org/wsvn/pkg-shadow/upstream/trunk/NEWS)

```

$Id: NEWS 3279 2010-08-29 19:02:41Z nekral-guest $

shadow-4.1.4.2 -> shadow-4.1.5                                  UNRELEASED

...
- newgrp, sg, groupmems
  * Fix parsing of gshadow entries.
...

```

EDIT:
Upstream BUG report:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=569899](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=569899)

> **kyoji said:**
> 
Next, after using `sudo gpasswd -A usr grp`, the user becomes an admin of the group, he can add/remove users only for that grp, but is not a "member". How would I find out who are admins of groups? I have tried `groups`, looking in /etc/group and theres nothing, the user does't even look like hes associated with the group at all.:confused:
 
I hope some one can clear this mystery up for me.

The third field in the /etc/gshadow file contains the coma-separated list of administrators. 

See:
```
man gshadow
```

---

### Post by kyoji on 2010-09-30
Your the man!!! Was starting to think I was never going to find an answer..

---

