---
title: "Getting Root Permissions"
date: 2012-04-26
forum: General Help
---

### Post by xTheAngrySockx on 2012-04-26
Hi all,

I'm just curious to know if there is a way to get root permissions on Ubuntu. I want to be able to run terminal based applications without the need of a 'sudo' prefix. If anybody knows how to do this or maybe even knows a link to a guide than that would be very helpful.

---

### Post by albandy on 2012-04-26
If you type sudo -s you will get a root session console.

---

### Post by nothingspecial on 2012-04-26
```
sudo -i
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Lars Noodén on 2012-04-26
Or you can set sudo to allow you to run just those specific applications without need of a password.

You can even limit the parameters passed to the applications.

```

%adm ALL=(ALL) NOPASSWD: /usr/bin/apt-get clean, /usr/bin/apt-get update, /usr/bin/apt-get upgrade, /usr/bin/apt-get dist-upgrade, /usr/bin/apt-get autoremove

```

---

### Post by xTheAngrySockx on 2012-04-27
Thank you all for you help.

---

### Post by raja.genupula on 2012-04-27
Please mark the thread as solved from thread tools , that could help us to look at other threads .


Thank you my friend .

---

