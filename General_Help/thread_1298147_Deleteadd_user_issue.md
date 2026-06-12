---
title: "Delete/add user issue"
date: 2009-10-22
forum: General Help
---

### Post by watson524 on 2009-10-22
I'll try to make this brief. I was working on a file sharing issue and got some great help on that. In the course of that, I set up an account with a user name of will and a password on the linux box and also added it to samba. Tested getting to a shared folder on the linux box from a windows machine that has the same login/password so when I went to the shared folder, it didn't prompt me for a login. To be sure it was working, I deleted the will account in admin/user groups on linux and created a will2. (The reason I did this was to test from windows machine if it would really prompt for password). Windows prompted and I put in WORKGROUP/will2 and the password but it wouldn't let me connect to share. Ok so I wanted to start over, deleted will2 account. Go back to add back in "will" account, it says it's already there, though it doesn't show it.

ran:
sudo userdel -r will
sudo rm -r /home/will

it deleted the home directoy but it still won't let me make either the will or the will2 accounts now. keeps telling me they already exist but it doesn't show them in admin/user groups.

thanks!

---

### Post by Iowan on 2009-10-22
Must be a typo in **man userdel**:>  userdel is a low level utility for [COLOR="Red"]adding[/COLOR] users. On Debian,
       administrators should usually use deluser(8) instead.
Anyway... Check */etc/passwd* and */etc/shadow* (this one will require **sudo**) to verify no user named will.

---

### Post by macabrem on 2009-10-22
You have to delete the group "will" also.  Then it will let you recreate will.

---

### Post by watson524 on 2009-10-22
> **macabrem said:**
> You have to delete the group "will" also.  Then it will let you recreate will.

This did the trick. Thanks so much!!

---

