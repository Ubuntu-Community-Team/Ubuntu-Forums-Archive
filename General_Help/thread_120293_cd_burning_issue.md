---
title: "cd burning issue"
date: 2006-01-21
forum: General Help
---

### Post by bernardfrancois on 2006-01-21
Hi,

I'm using K3B to burn CD's, but probably the same problems will occur for any other cd burning appication...

I have two users on my computer, *julie* and *ber*.

How to re-produce the issue I'm talking about:

1) I log in with *julie*, and then switch to *ber* (*julie*'s still logged in)
2) I put a blank cd-r in the cd-writer.
3) I won't be able to burn any cd's; my cd burning application will say 'only julie can unmount the cd'

So I guess the first logged-in user detects the cd first and mounts it? (only the user that mounted a device can unmount it).

Anyone who knows how to change this behaviour? I would still like to use the automatic mounting...

---

### Post by aysiu on 2006-01-21
Is Julie the first user you created?

---

### Post by bernardfrancois on 2006-01-22
No. *ber* was the first user, *julie* was created afterwards.

---

### Post by aysiu on 2006-01-22
Try this.
Log in as Julie and go to System > Administration > Users and Groups.
Double-click on Ber.
Go to User Privileges and make sure everything's checked.

If that doesn't work, try logging in as Julie and going to Applications > Accessories > Terminal and typing ```
sudo adduser ber admin
```

---

### Post by bernardfrancois on 2006-01-24
This is the reply I wanted to post two yesterday, but the forum seemed to be offline...

[quote=me, yesterday]
Note that *julie* doesn't have the permission to 'execute system administration tasks', so the account doesn't have the right to use *sudo* or the *Users and groups* front-end.

I checked those things using the *ber* account, and both *julie* and *ber* have the proper rights.

I just did another test: As *ber*, I put a cd in the tray. Right after that, I tried to unmount it in nautilus. It doesn't work (again, *julie* was also logged in).

This is the message I get (in a messagebox):

umount: only julie can unmount /dev/hdb from /media/cdrom0
eject: unmount of `/media/cdrom0' failed
[/quote]


Today I tried it again: I first logged in as *ber*, then I logged in as *julie*. Under *julie*, I inserted a CD. I tried to unmount it, and it didn't work. The same message appeared: 'only ber can unmount ...'.
Then I switched again to *ber*, I removed the CD and inserted it again. I tried to unmount, and it worked.
I inserted the CD again, and I couldn't unmount.

It seems like the two instances of X (or aren't it two instances of X?) try both to mount the CD. The one that mounts it first, 'wins'...

[edit]
I just tried this in the other CD drive of the two I have in my computer (one is a philips cd writer, the other is some dvd reader), and the same thing happened (the other user mounted it).
[/edit]

---

