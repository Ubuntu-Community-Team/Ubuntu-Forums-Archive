---
title: "Can't load synpatic from shortcut."
date: 2006-04-06
forum: General Help
---

### Post by zend on 2006-04-06
I have a root account.  If I run synaptic from console it works fine.  When I click on the shortcut, it asks for the password.  I type it in and the synaptic window does not appear.  Nothing happens.  If I click on it again it doesn't ask for the password, and absolutely nothing happens.

---

### Post by aysiu on 2006-04-06
What's the output when you run this command from terminal? ```
gksudo synaptic
```

I'm assuming you normally do ```
su
password:
synaptic
```

---

### Post by zend on 2006-04-06
After I type in the root password a message box pops up and says:
Failed to run synaptic as user root:
 The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator.

---

### Post by zend on 2006-04-07
Bump

---

### Post by aysiu on 2006-04-07
It sounds as if something's wrong with your /etc/sudoers file.

Maybe [this](http://ubuntuforums.org/showthread.php?t=14366) will help? Read the **whole** thread.

---

