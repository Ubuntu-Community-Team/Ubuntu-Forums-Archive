---
title: "Problems with exotic user/group names?"
date: 2009-12-28
forum: General Help
---

### Post by shade5 on 2009-12-28
Hi,
I read in a real old Linux book that you should not use more than 8 chars for a name since most programms only cooperate with 8. Also you should avoid exotic asciis. Is this still the case? How do you use symbols like . , ! anyway?

Thanks

---

### Post by dcstar on 2009-12-28
> **shade5 said:**
> Hi,
I read in a real old Linux book that you should not use more than 8 chars for a name since most programms only cooperate with 8. Also you should avoid exotic asciis. Is this still the case? How do you use symbols like . , ! anyway?

Thanks

```
man adduser.conf
```

---

### Post by shade5 on 2009-12-28
Thanks now I only need to know which problems occure with names longer than 8 chars.

---

### Post by Albert Net on 2010-06-13
I don't know what problems there will be if there are more than 8 characters, but I guess there should not be any problem, since my user name contains 9 characters.


Here is one interesting problem, at the bottom line of /etc/adduser.conf,

NAME_REGEX="^[a-z][-a-z0-9]*\$"


The backslash is very weird here. 

In my experiment, this regular expression requires '$' in the user name.

I thing this backslash should be removed.

---

