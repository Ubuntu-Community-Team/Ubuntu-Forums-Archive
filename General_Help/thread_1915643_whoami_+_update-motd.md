---
title: "whoami + update-motd"
date: 2012-01-26
forum: General Help
---

### Post by Ateo on 2012-01-26
Hello,

I have this in /etc/update-motd.d/10-header:
```
#!/bin/sh

printf "Successfully logged in as %s on %s (%s)\n" "$(id -un)" "$(hostname)" "$(lsb_release -s -d)"

exit
```

When I log in as a regular user, this is the message:
> Successfully logged in as root on orion (Ubuntu 11.10)

I'm trying to figure out why $(id -un) is returning user 'root' instead of the user actually logging in. I've also tried $(whoami) which produces the same output.

Ideas as to why update-motd is reporting the wrong user from both terminal and ssh? For what it's worth, I've completely disabled root login for OpenSSH.

Thanks.

---

### Post by CharlesA on 2012-01-26
Probably because update-motd is running as root.

Just guessing ;)

You could try having it use $USER instead.

---

### Post by Ateo on 2012-01-27
That's a good guess but $USER produces root as well. Oh well, not important I guess. i'll just omit the "user" part of that output.

Thanks anyways. =)

---

### Post by CharlesA on 2012-01-27
Hrm, you got me curious now. I think it acts like it does because it creates the motd ahead of time, instead of on login.

The motd I [wrote up]("http://charlesa.net/scripts/linux/custommotd.php"), would run on logon, which would slow the login time down a bit.

---

### Post by Ateo on 2012-01-27
yea, it is curious. it should display the user but i guess it is probably that the script runs right before final authentication. just guessing though...

---

### Post by CharlesA on 2012-01-27
> **Ateo said:**
> yea, it is curious. it should display the user but i guess it is probably that the script runs right before final authentication. just guessing though...
That is what I think as well.

---

