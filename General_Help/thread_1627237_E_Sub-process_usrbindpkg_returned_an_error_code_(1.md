---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2010-11-21
forum: General Help
---

### Post by mori64 on 2010-11-21
E: Sub-process /usr/bin/dpkg returned an error code (1)
when i want to update or upgrade this error appears
well i Googled and i saw  [URL="http://ubuntuforums.org/showthread.php?t=21672"]http://ubuntuforums.org/showthread.php?t=21672
[/URL] but may harddrive isn't full
 
mori@lol:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda6             18326876   7290552  10105360  42% /
none                    379064       304    378760   1% /dev
none                    383400       372    383028   1% /dev/shm
none                    383400        96    383304   1% /var/run
none                    383400         4    383396   1% /var/lock
none                    383400         0    383400   0% /lib/init/rw

so what can i do?

---

### Post by mori64 on 2010-11-21
no one could help me ?!:cry:

---

### Post by sikander3786 on 2010-11-21
Please post the output of

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

That would tell us about the offensive/mis-configured packages.

Please post the complete output and wrap it with proper code tags # from the post menu. ```

``` Paste it between those codes.

---

### Post by mori64 on 2010-11-22
thank u but the problem solved ;)
grub had got problem

---

