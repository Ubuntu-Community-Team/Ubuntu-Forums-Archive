---
title: "PHP shell_exec() as Root"
date: 2010-10-10
forum: General Help
---

### Post by Hovercat on 2010-10-10
Hi.  I understand the risks of running commands to the server as root, so don't give me any crap about that.  This is my PHP script:

```

<?php

$ip = $_POST['ip2ban'];

shell_exec('iptables -I INPUT -s '. $ip .' -j DROP');
shell_exec('iptables-save');

Echo "IP ban added sucessfully."

?>
```

And I need it to run both of those commands as root.  I already tried adding stuff into sudoers, but when I run sudo commands in the terminal:  



```
burns@asskickersunited-server:~$ sudo iptables -L
>>> /etc/sudoers: syntax error near line 29 <<<
sudo: parse error in /etc/sudoers near line 29
sudo: no valid sudoers sources found, quitting
```

I already tried chmod 4711 and chown root:root.

---

### Post by blazemore on 2010-10-10
The error message "Syntax Error" means there's a problem with the way you edited the /etc/sudoers files.
Please post your sudoers file here and someone will be able to see what the problem is.

---

### Post by Hovercat on 2010-10-10
My sudoers file is currently at default.

I don't have what it used to be any more.

---

