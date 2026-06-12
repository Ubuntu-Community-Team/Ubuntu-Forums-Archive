---
title: "Software Center permissions"
date: 2009-11-29
forum: General Help
---

### Post by Leppie on 2009-11-29
Hi all,

not sure this is the right place for this thread, if not I'd like to ask the mods to kindly move it into the right section.

I've installed software center to have a go with it and everything went well. I can install, remove, search, etc.
However, I have some users who aren't in the admin group who I would like to give access to software center as it seems an easy to use tool. I created a group for these users and added it to the sudoers file listing software center as an authorized application for that group. Software center opens and the users from that group can browse the packages and select those they would like to install. But when they click install a policy kit authorization screen pops-up stating the application needs super user rights in order to proceed. I tried adding policy kit to the sudoers file, but no luck.

Anybody knows how to solve this issue?
Many thanks in advance :P

---

### Post by Leppie on 2009-11-29
Anybody please?

---

### Post by berarma on 2010-04-30
I'll be trying this soon. Did you solve your problem?

---

### Post by Leppie on 2010-05-13
no, i've never managed to setup normal users to use software center. not being able to setup normal users to only use software center actually seems to defeat the purpose of the whole thing...

---

### Post by sisco311 on 2010-05-13
Create a new .pkla file:
```
gksu gedit /var/lib/polkit-1/localauthority/50-local.d/software-center.pkla
```


Add something like this to the file:
```

[Installing software]
Identity=unix-group:**groupname**
Action=org.debian.apt.install-packages;org.debian.apt.update-cache
ResultActive=auth_self_keep

```

Save the file & close it. That's all.


For a list of other actions run:
```
pkaction --verbose | less
```

---

### Post by Leppie on 2010-06-28
just tried this, working like a charm.
many thanks [sisco311]("http://ubuntuforums.org/member.php?u=244665")

---

