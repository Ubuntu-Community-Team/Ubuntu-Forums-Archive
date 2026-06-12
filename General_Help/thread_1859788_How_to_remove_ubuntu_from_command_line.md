---
title: "How to remove ubuntu from command line"
date: 2011-10-14
forum: General Help
---

### Post by nguyenabcd on 2011-10-14
I installed ubuntu from CD. I choose install it alongside Win 7.  One day, I edited my .profile and I can't login since then.  How I can remove it from comman line. I'm new to ubunto, so please tell me clearly as much as  possible.

---

### Post by matt_symes on 2011-10-14
Hi

> **nguyenabcd said:**
> I installed ubuntu from CD. I choose install it alongside Win 7.  One day, I edited my .profile and I can't login since then.  How I can remove it from comman line. I'm new to ubunto, so please tell me clearly as much as  possible.

Boot into recovery console (root console) from the grub menu.

Then type

```
cp /etc/skel/.profile /home/<your_user_name>
```

Change <your_user_name> to your user name.

Then type

```
reboot
```

Kind regards

---

### Post by nguyenabcd on 2011-10-15
I choose recovery mode, 
choose resume normal boot
I inputed my user and password
I saw line error and some content in .profile which make me get error

But when I type
cp /etc/skel/.profile /home/<your_user_name>
it doesn't work. Maybe it require some paramater.?
What aboe intruction mean?

---

