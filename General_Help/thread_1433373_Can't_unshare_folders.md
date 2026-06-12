---
title: "Can't unshare folders"
date: 2010-03-18
forum: General Help
---

### Post by thomashw on 2010-03-18
I created a shared folder in my network, and then unshared it but it still shows up on Guest computers and people can still access it.

How can I stop the share? "Sharing options" is completely greyed out.

---

### Post by thomashw on 2010-03-19
Bump.

---

### Post by Morbius1 on 2010-03-19
What does the following command output:

**net usershare info**

---

### Post by thomashw on 2010-03-20
```

[complete downloads]
path=/home/thomas/Downloads/complete
comment=
usershare_acl=Everyone:F,
guest_ok=y

[incomplete downloads]
path=/home/thomas/Downloads/incomplete
comment=
usershare_acl=Everyone:F,
guest_ok=y

```
For the folders "complete" and "incomplete", if I go to their sharing options, both are unchecked and greyed out.

What can I do?

---

### Post by thomashw on 2010-03-20
> **thomashw said:**
> ```

[complete downloads]
path=/home/thomas/Downloads/complete
comment=
usershare_acl=Everyone:F,
guest_ok=y

[incomplete downloads]
path=/home/thomas/Downloads/incomplete
comment=
usershare_acl=Everyone:F,
guest_ok=y

```
For the folders "complete" and "incomplete", if I go to their sharing options, both are unchecked and greyed out.

What can I do?
I found config files for these shares in /var/lib/samba/usershares. One is named "complete downloads" and the other is named "incomplete downloads".

Is it safe to simply delete these files, or does more need to be done?

---

### Post by Morbius1 on 2010-03-20
Yes you can delete them from /var/lib/samba/usershares.

You really should have gotten an error when you initially created those shares. In the future you might want to follow two rules in share creation:

Share names should be 12 characters or less.
Share names should not have spaces in them. OK, that's not really a rule but it will save you aggravation in the long run - Linux hates spaces.

---

### Post by thomashw on 2010-03-20
Thanks a lot. :)

---

### Post by smuthavarapu on 2012-04-15
Thank you that is useful information. Solved my issue too.

---

