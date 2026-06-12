---
title: "User Password Change Failed"
date: 2009-12-16
forum: General Help
---

### Post by Heeney.CS on 2009-12-16
Hi there,

I finished setting up my daughters laptop with Ubuntu 9.10 and then went into System->Administration->Users and Groups, and proceeded to change the password.

I logged off and logged back in with the new password but I could only use the old one. When I logged in with the old password i had a new pop-up window "Unlock Keyring". This new pop-up wants the new password that I entered in order to make my wireless connection.

How can I get this back to where it used to be so the "Unlock Keyring" window does not appear? I assume the password for this application has to be reset somehow.

Thanks,

Chris

---

### Post by whiteychs on 2009-12-16
[http://ubuntu-tutorials.com/2007/07/12/automatically-unlocking-the-default-gnome-keyring-pam-keyring/](http://ubuntu-tutorials.com/2007/07/12/automatically-unlocking-the-default-gnome-keyring-pam-keyring/)

---

### Post by Heeney.CS on 2009-12-16
@whiteychs
Thanks for your response.

I also found this blog post which resolved the problem: [http://www.greenhughes.com/content/how-change-default-keyring-password-ubuntu-netbook-remix-904](http://www.greenhughes.com/content/how-change-default-keyring-password-ubuntu-netbook-remix-904)

There is obviously a bug with the password management system though. I new there was a bug when trying to change the logon password of an encrypted home directory but not a normal one.

So it looks like for now you can't change your password until this bug is fixed. At least i was able to get this back to its original state.

Thanks for the help :)

Chris:)

---

### Post by whiteychs on 2009-12-16
You could always change the password from the terminal.

[http://www.cyberciti.biz/faq/linux-set-change-password-how-to/](http://www.cyberciti.biz/faq/linux-set-change-password-how-to/)

---

