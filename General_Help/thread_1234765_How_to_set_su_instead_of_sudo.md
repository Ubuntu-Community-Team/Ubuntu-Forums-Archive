---
title: "How to set su instead of sudo"
date: 2009-08-08
forum: General Help
---

### Post by Disident on 2009-08-08
Hi. I'd like to have standard su system instead of sudo.
I already enabled root user:
# passwd root
and add comment in front of "%admin ALL=(ALL) ALL" so now I have only:
Defaults env_reset
root ALL=(ALL) ALL

but now problem is that if I'm asked graphically to enter password (for example to install hardware drivers via GUI) both passwords (root and user) don't work.
I even tried to set root user as admin but didn't do the trick.
can someone please tell my how to have that super-user system like in Debian for instance?
thanks

---

### Post by lisati on 2009-08-08
Please read [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Disident on 2009-08-08
Thank you for the link, but I already wrote "man sudo_root" as well as that article you posted and still no answer there..

---

### Post by sisco311 on 2009-08-08
```
gksu-properties
```
and set the authentication mode to su.

---

### Post by Disident on 2009-08-08
sisco311, You're the Man!! thank you very much !:)

---

### Post by sisco311 on 2009-08-08
NetworkManager and users-admin(Users and Groups) uses PolicyKit for authentication. You will have to edit the /etc/PolicyKit/PolicyKit.conf file to something like this:
```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- XML -*- -->

<!DOCTYPE pkconfig PUBLIC "-//freedesktop//DTD PolicyKit Configuration 1.0//EN"
"http://hal.freedesktop.org/releases/PolicyKit/1.0/config.dtd">

<!-- See the manual page PolicyKit.conf(5) for file format -->

<config version="0.1">
    <match user="root">
        <return result="yes"/>
    </match>
    <define_admin_auth **user="root"**/>
</config>

```

Also you can set sudo to prompt for the root password by appending the *Defaults* line in the sudoers file with *rootpw*:
```
Defaults        env_reset,rootpw
```

---

### Post by Disident on 2009-08-08
Thank you once more, so far all is working good :)

---

