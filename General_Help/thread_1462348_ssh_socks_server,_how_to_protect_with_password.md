---
title: "ssh socks server, how to protect with password?"
date: 2010-04-25
forum: General Help
---

### Post by aytacaksel on 2010-04-25
first i'm realy new for ubuntu/linux.. p

ssh -NCfgD 1080 user@host command creating great proxy server and i can connect it from windows 7 with sockscap. problem is that server isnt asking for password. everyone can connect. i wanna protect it with password. my windows ip is dynamic.

already tryed dante-server but realy bad performance

---

### Post by aytacaksel on 2010-04-26
anyone? :)

---

### Post by ibuclaw on 2010-04-26
Does the server have an authorized_key file?
```
~/.ssh/authorized_key
```

If so, that and the options set in /etc/ssh/sshd_config
```

RSAAuthentication yes
PubkeyAuthentication yes

```
Could be one reason this is happening.

Regards

---

### Post by aytacaksel on 2010-04-26
[FONT=monospace]created authorized_key file, options already set, rebooted server.

used ssh -NCfgD 31080 command

socks 5 server still dont asking password :(
[/FONT]

---

### Post by ibuclaw on 2010-04-26
> **aytacaksel said:**
> [FONT=monospace]created authorized_key file, options already set, rebooted server.

used ssh -NCfgD 31080 command

socks 5 server still dont asking password :(
[/FONT]

Creating that file and setting those options is one way to **disable** password authentication. I did not at all suggest you do that, merely check that it hasn't been set.

---

