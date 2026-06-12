---
title: "Help with setting up a web server"
date: 2011-12-19
forum: General Help
---

### Post by adamantasaurus on 2011-12-19
Hello,

I am trying to follow this tutorial ......

[http://www.howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-3-p3](http://www.howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-3-p3)

 I am at the part where it says ......

```

echo server1.example.com > /etc/hostname
/etc/init.d/hostname restart

```

When I hit enter on my computer it tells me that my permission is denied and I typed sudo.

Do you know why this is saying this? 

(I'm using ubuntu server 10.04)

Thank You

Adamantasaurus

---

### Post by killermist on 2011-12-19
If I understand permissions, the superuser privileges are applied to the command and not to the redirection of the output.
You may want to 
```
sudo su
echo server1.example.com > /etc/hostname
/etc/init.d/hostname restart
exit

```
That way, all the commands are issued as root, and then the root privileges are dropped immediately.

---

### Post by adamantasaurus on 2011-12-19
thanks that worked

---

