---
title: "bashrc ls alias not working same as command line"
date: 2010-10-25
forum: General Help
---

### Post by mancocapac on 2010-10-25
Hi,

I have a few alias' in my .bashrc to save some typing, mostly ls type variants. 

I wanted to add the following: 
- give me a Long listing of ALL in Reverse Time order, (don't recurse directory)
```

alias lsrt='ls -a1rt'

```But it doesn't work anything like the way it does on the command line

When I use the alias I get the following:
```

Videos
Templates
Music
Documents
Desktop
.dbus
.pulse-cookie
.esd_auth
...

```No Time, No Permissions, no group/owner ... , Why?

Thanks

---

### Post by WorMzy on 2010-10-25
Your 1 in "-a1rt" is a one, not a lowercase L. It should be the latter.

---

### Post by mancocapac on 2010-10-25
thanks! I looked at the 20 times and didn't see it

---

