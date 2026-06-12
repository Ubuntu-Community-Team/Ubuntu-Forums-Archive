---
title: "Advanced adding of a user via Terminal"
date: 2012-02-20
forum: General Help
---

### Post by Floore on 2012-02-20
Hi everyone,

I have a problem that seems to not actually be possible to solve. I need to be able to do the following:

1. Create a user 'dave' with an automatically generated password, that is not asked for on login, and assign to a group 'limited'
2. Change the login screen to not show the list of users
3. Automatically login using the limited user's account
4. Set a timeout on the automatic login so the admins can login if necessary

I can do all of this in Ubuntu, of course, but is there a way to make all of these changes via the command line?? So far I have a small script for creating the user's group, creating the user account, and assigning the user to a group, I can't figure out how to change all the other things via a script though, is this possible?

Thanks in advance,

Tom

---

### Post by Cheesehead on 2012-02-20
> **Floore said:**
> Hi everyone,
2. Change the login screen to not show the list of users


According to [http://askubuntu.com/questions/68953/dont-list-all-users-at-login-with-lightdm](http://askubuntu.com/questions/68953/dont-list-all-users-at-login-with-lightdm) ,```
$ sudo -u gdm gconftool-2 --type boolean --set /apps/gdm/simple-greeter/disable_user_list true
```

---

### Post by Floore on 2012-02-20
My apologies,

I should have mentioned that I have managed to get the list of users to also disappear. My main problem is adding the login delay, and setting the account to have a randomly generated password.

Regards,

Tom

---

