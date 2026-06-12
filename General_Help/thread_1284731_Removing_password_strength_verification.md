---
title: "Removing password strength verification"
date: 2009-10-06
forum: General Help
---

### Post by orlox on 2009-10-06
I have a system whose security isn't really a concern, yet I require a user password, so when I lend my computer to someone in my family, they won't brick it...So, when I install ubuntu in this computer, I usually set a very simple password. I can set this password when installing ubuntu (though it warns me it's not secure), but now I created a new account, and I can't find a way to set a simple password, every time I set one, it says it's too unsecure or too short...

I also tried directly using passwd, yet, the same problems arise. I believ this restrictions are setted by pam, and can be modyfied in order to remove (or reduce) this password strength verification, yet I haven't found a way to do this yet...

---

### Post by c0mput3r_n3rD on 2009-10-06
Linux makes you have a pass word of I think at least 6 characters...

---

### Post by kavon89 on 2009-10-07
Only full root can set a weak password, even if it's a single character:

```
[kavon@thinkpad-r61 ~]$ su -
Password: 
[root@thinkpad-r61 ~]# passwd kavon
Changing password for user kavon.
New password: 
Retype new password: 
BAD PASSWORD: it is WAY too short
BAD PASSWORD: is a palindrome
passwd: all authentication tokens updated successfully.
[root@thinkpad-r61 ~]# 
```

I believe su/root is locked or disabled in Ubuntu (I'm using Fedora). Look into enabling it somehow and you'll be golden.

---

### Post by orlox on 2009-10-07
> **kavon89 said:**
> Only full root can set a weak password, even if it's a single character:

```
[kavon@thinkpad-r61 ~]$ su -
Password: 
[root@thinkpad-r61 ~]# passwd kavon
Changing password for user kavon.
New password: 
Retype new password: 
BAD PASSWORD: it is WAY too short
BAD PASSWORD: is a palindrome
passwd: all authentication tokens updated successfully.
[root@thinkpad-r61 ~]# 
```

I believe su/root is locked or disabled in Ubuntu (I'm using Fedora). Look into enabling it somehow and you'll be golden.

Excellent! thanks

---

