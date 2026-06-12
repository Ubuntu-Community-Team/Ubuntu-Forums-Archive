---
title: "apache2 reload problem"
date: 2009-09-01
forum: General Help
---

### Post by ac13 on 2009-09-01
I have a short shell script that is supposed to reload apaches config but nothing happens, no error message, nothing.
I have tried writing the following line/lines in the shell script.

```
RELOAD="sudo /etc/init.d/apache2 reload"
$RELOAD
```

```
sudo /etc/init.d/apache2 reload
```

if I would to manually reload apache in bash with sudo /etc/init.d/apache2 reload it works but not with the script! :confused:

---

### Post by credobyte on 2009-09-01
Check [http://forums.macosxhints.com/showthread.php?t=42593](http://forums.macosxhints.com/showthread.php?t=42593) - might solve your problem.

---

### Post by ac13 on 2009-09-01
Thanks! :D

To document the solution I added this line to the sudoers file.
Works like a charm.

```
www-data ALL=(ALL) NOPASSWD:/etc/init.d/apache2 reload
```

---

