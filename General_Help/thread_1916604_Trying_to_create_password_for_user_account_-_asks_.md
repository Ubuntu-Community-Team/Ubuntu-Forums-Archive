---
title: "Trying to create password for user account - asks for non existent current password"
date: 2012-01-28
forum: General Help
---

### Post by oktorockto on 2012-01-28
Have 11.10. 4 user accounts. 2 Admin and two standard. One of the standard accounts has a password. The other standard account has never had a password. Now I want to add a password but when I try to do it using the set a password now option in the User Accounts window it asks for the current password. There never was one! Pulliing my hair out with this one...

---

### Post by Cheesemill on 2012-01-28
What happens if you just leave that box blank?

If that doesn't work you could always do it from the command line:
```
sudo passwd username
```

---

### Post by sudodus on 2012-01-28
I suggest that you use the terminal command passwd, assuming the username is susan, type

```
sudo passwd susan
``` enter your password, and then enter the (new) password for the username twice.

Read this link for more info
[[COLOR="Red"]_http://www.psychocats.net/ubuntu/resetpassword_[/COLOR]]("http://www.psychocats.net/ubuntu/resetpassword")

---

### Post by oktorockto on 2012-01-29
Thanks very much. I tried the sudo passwd username method and it did indeed allow me to set a password and this was confirmed by going back into user accounts in system settings where I can now set any password I want for that account as I now have a current password.

However, at boot up, when the login screen appears, there is still no password field for that particular user account. Just a login button which lets you straight into that user account with no password protection.

Any ideas?

---

### Post by sudodus on 2012-01-30
Can you do what you want with help from this link?

[http://ubuntuguide.net/how-to-login-without-password-in-ubuntu-11-10](http://ubuntuguide.net/how-to-login-without-password-in-ubuntu-11-10)

You should reverse it, deselect login without a password.

---

