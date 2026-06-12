---
title: "cannot restart samba"
date: 2006-04-06
forum: General Help
---

### Post by renzokuken on 2006-04-06
i definately have samba installed and it must be working because i can see the winxp pcs on the network.

the XP machines however cannot see me, so i edited my smb.conf a bit and am now trying to restart samba with the command 

```
sudo /etc/init.d/samba restart
```

but its not working, all i get is the error

"sudo: /etc/init.d/samba: command not found"

does this mean my samba is not installed properly?

---

### Post by spanishwasabi on 2006-04-07
Are you sure you installed the server *and* the client packets?

It looks like you only installed the client utilities.

Have a look at:
[http://www.howtoforge.com/samba_setup_ubuntu_5.10_p4](http://www.howtoforge.com/samba_setup_ubuntu_5.10_p4)

Enjoy,

G

---

### Post by renzokuken on 2006-04-07
its ok, i solved this now, had some problems with synaptic that wasnt installing programs completely.

---

