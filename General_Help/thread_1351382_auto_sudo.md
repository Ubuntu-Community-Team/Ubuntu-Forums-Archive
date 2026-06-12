---
title: "auto sudo"
date: 2009-12-10
forum: General Help
---

### Post by loki_dre on 2009-12-10
how do I automatically input the password after a sudo command?

---

### Post by lisati on 2009-12-10
> **loki_dre said:**
> how do I automatically input the password after a sudo command?

I would counsel against doing this automatically - it's there for your protection, a bit like "are you sure?"

Having said that, your password will be remembered for a short while (usually about 15 minutes or so) so you won't have to put it in every time.

There are other options, some of which are mentioned here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by hwttdz on 2009-12-10
You can either edit the sudoers file or you can use an askpass argument.  If this doesn't immediately make sense to you then you probably want sudo there as an idiotcheck to make sure you don't break your own system.

---

### Post by lisati on 2009-12-10
> **hwttdz said:**
> You can either edit the sudoers file or you can use an askpass argument.  If this doesn't immediately make sense to you then you probably want sudo there as an [COLOR="Red"]idiotcheck[/COLOR] to make sure you don't break your own system.
Where do I get one?

Good advice!

---

### Post by NFblaze on 2009-12-10
^^ Um.. that means dont mess with your current sudo settings.

---

### Post by loki_dre on 2009-12-10
thanks,
that worked

----------------------------------------------------------------------
solution:

Open a Terminal window. Type in **sudo visudo**. Add the following line to the END of the file (if not at the end it can be nullified by later entries): 
<username> ALL=NOPASSWD: ALLReplace <username> with your user name (without the <>). This is assuming that Ubuntu has created a group with the same name as your user name, which is typical. You can alternately use the group *users* or any other such group you are in. Just make sure you are in that group. This can be checked by going to **System->Administration->Users and Groups** 
Example: 
michael ALL=NOPASSWD: ALL
----------------------------------------------------------------------
reference: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

