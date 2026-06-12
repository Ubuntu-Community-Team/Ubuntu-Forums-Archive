---
title: "What's the difference between using mount and /usr/bin/udisks --mount"
date: 2012-07-22
forum: General Help
---

### Post by Matt Pellegrini on 2012-07-22
I've just learnt how to use mount and umount and very basic use of fstab. Then i discovered udisks and that way of mounting and handling mount issues. What's the difference and which should I use?


Thanks,

Matt

(Edit) I should point out that I understand that they achieve the same general task, my question is really is one better/ newer/ deprecated and why.

---

### Post by Paddy Landau on 2012-07-24
[FONT=Lucida Console]mount[/FONT] and [FONT=Lucida Console]umount[/FONT] simply mount and dismount devices.

[FONT=Lucida Console]udisks[/FONT] provides a raft of extra functions, such as monitoring, listing, spinning down, waking up, and ejecting. It also allows you to mount and dismount without elevated root privileges.

Use the command [FONT=Lucida Console]man[/FONT] [FONT=Lucida Console]udisks[/FONT] to find out more.

EDIT: In answer to your edit, simply use whichever you are more comfortable with.

---

### Post by Matt Pellegrini on 2012-07-24
Thanks, that's pretty concise, since I've learnt a fair bit using mount and umount, I'll continue using that.

Thanks again.

---

