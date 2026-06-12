---
title: "&lt;USER&gt; is not in the sudoers file. This incident will be reported."
date: 2012-01-19
forum: General Help
---

### Post by goodbye-windows(tm) on 2012-01-19
Hi All,

I am having a problem with the sudoers file, and after reading the official documentation and various posts on the forum, I'm more lost than I was when before all the reading::>

My daughter has her own computer, but I do not allow her to be an administrator. The other day, I was trying to follow the forums instructions for allowing her to play encrypted cd's. This requires the sudo command.

While logged in as a standard under, I entered the first command via the terminal. I was immediately asked for a password, I entered my administrator password. The response was:

**<USER> is not in the sudoers file. This incident will be reported.**

I was hoping that my administrators password would allow me to make the necessary changes without having to log in to the administrators account .

Is it possible to carry out commands requiring the superusers password while logged in as a standard user, or is it just not possible to do so for security reasons? If it is possible to use the sudo command while logged in as a standard user, what changes do I need to make to the system?


Regards,

Art


System is a Dell 15R, 64 bit, using unity, 11.10, i5 processor. The windows 7 os was deleted and only ubuntu is installed. There are 2 users on the system, my daughters standard user and my own administrator account. The home folder is encrypted, with the encryption enabled at the time of the original installation.

---

### Post by nothingspecial on 2012-01-19
While logged into her account, you can switch to your user in a terminal to administer.

```
su user
```

where user is your actual username. She might be a little upset come christmas time though

[http://xkcd.com/838/](http://xkcd.com/838/)

---

