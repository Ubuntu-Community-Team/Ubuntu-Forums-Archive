---
title: "Administration Panel Tools Locked !!"
date: 2010-01-20
forum: General Help
---

### Post by Bender_cr on 2010-01-20
Hi Guys have a quick question I have ubuntu server, I did install ubuntu-desktop and then no-machine so I can have GUI, but when I try to use an administrative tool like network-admin or time-admin the unlock button is grayed out so I can use it, I'm running on a different user because no machine will not allow to log in as root user, I'm sure this user is in the sudoers file, but still unable to use the panels, any suggestion ??
[IMG]http://img130.imageshack.us/img130/8281/unlock.jpg[/IMG]

Thanks in advance

---

### Post by sisco311 on 2010-01-20
Is your user in the admin group?

```
id
```

Can you use pkexec?
```
pkexec echo "works"
```

What's the output of:
```
cat /etc/polkit-1/localauthority.conf.d/*
```?

---

### Post by Bender_cr on 2010-01-21
Hi this are the results


id

```
 gid=1000(trinity) groups=1000(trinity)
```


Can you use pkexec?
```
command not found
```


What's the output of:

```
cat: /etc/polkit-1/localauthority.conf.d/*: No such file or directory
```

---

### Post by sisco311 on 2010-01-21
Boot in the Recovery Mode and add your user to the admin group:
[http://psychocats.net/ubuntu/fixsudo](http://psychocats.net/ubuntu/fixsudo)

---

