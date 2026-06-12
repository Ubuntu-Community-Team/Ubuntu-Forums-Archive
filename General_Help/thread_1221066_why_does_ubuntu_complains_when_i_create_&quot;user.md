---
title: "why does ubuntu complains when i create &quot;user.name&quot;?"
date: 2009-07-23
forum: General Help
---

### Post by ruipedroca on 2009-07-23
hi,

why does ubuntu complains when i create "user.name"?

i mean, in fedora we can creat users with "." in the middle of the username

why can't we do it on ubuntu?
(i know we can force ubuntu to do it, but will that give me any troubles?...)


regards

---

### Post by Zorael on 2009-07-23
Convention, I guess. The setting is in /etc/adduser.conf, commented out.
```
# check user and group names also against this regular expression.
#NAME_REGEX="^[a-z][-a-z0-9]*\$"
```
man adduser.conf says:
```
       NAME_REGEX
              User  and  group  names  are  checked  against  this regular
              expression. If the name doesn't match this regexp, user  and
              group  creation in adduser is refused unless --force-badname
              is set. With --force-badname set, only weak checks are  per&#8208;
              formed.  The  default  is  the  most conservative [B]^[a-z][-a-
              z0-9]*$[/B].  When --system is specified,  NAME_REGEX_SYSTEM  is
              used instead.
```
Change it in that file if you want to get rid of the warning. My regex fu is weak.

---

### Post by ruipedroca on 2009-07-23
Hi Zorael,

Thanks for your clear explanation :)

But please answer this:
will i get into any troubles if i force the system to accept a new user named "name.name"?


Best Regards

---

### Post by ruipedroca on 2009-07-24
Doesn't anybody know?...:confused:

---

