---
title: "How can a Desktop User deletes www-data files?"
date: 2010-12-26
forum: General Help
---

### Post by emurad on 2010-12-26
Hello,

I have some developers with Desktop User accounts. How can I allow them to delete files owned by www-data which are created under their accounts (/home/username/public_html) by PHP scripts they are coding and testing.

I tried to edit www-data user group and add the user as a member of it but this has no effect - the user still unable to delete these files only by creating another PHP script!

Thanks.

---

### Post by kidders on 2010-12-27
Hi there,

> **emurad said:**
> I tried to edit www-data user group and add the user as a memberThat's not a good idea ... you should undo that change.

Assuming each user owns his own ~/public_html, they can already delete files put there by other users, so unless you have an unusual set-up, you shouldn't need to do anything. If you wanted to give developers a little more flexibility, you could always set their ~/public_html directories' SGID bits. For example ...```
# cd /home
# for f in *; do chown $f:$f $f/public_html; chmod g+sw $f/public_html; done
```

That's nothing the individual users can't do themselves, if they wanted to allow their scripts to grant them write access to files as they're created (rather than just permission to delete them).

I hope that helps.

---

