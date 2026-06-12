---
title: "Disable live user on liveusb"
date: 2011-07-04
forum: General Help
---

### Post by dewdrop_world on 2011-07-04
When I boot from a live USB, it automatically logs in as the live user. I don't want that. I want to log in as a real user, without having to log out of the live user session first.

I looked at all the options under system > administration > users&groups. Nothing seems applicable.

Any ideas?

*edit* PS, I did already create the real user and it's working fine. I just have to log out before I can log in as the right user.

---

### Post by mikejonesey on 2011-07-04
an option under menu->sys->admin->users n groups;

then select password on the user you wish to disable auto login and uncheck that option...

---

### Post by dewdrop_world on 2011-07-04
> **mikejonesey said:**
> an option under menu->sys->admin->users n groups;

then select password on the user you wish to disable auto login and uncheck that option...

That's already unchecked. It still logs in as the live user.

After logging in as the real user, the live user no longer appears in the u&g panel.

---

### Post by mikejonesey on 2011-07-04
did you allocate disk space on your usb for saving changes when you created it? other than that only thing i can think of is try and change the password on the same menu with the option to disable auto login...

---

### Post by C.S.Cameron on 2011-07-04
Creating a new user in users and groups should automatically remove the Live user Ubuntu.

---

### Post by mikejonesey on 2011-07-05
will test tomoz see if i can see nethin...

---

