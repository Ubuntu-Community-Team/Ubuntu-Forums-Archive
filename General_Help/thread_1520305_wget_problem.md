---
title: "wget problem"
date: 2010-06-29
forum: General Help
---

### Post by nour02 on 2010-06-29
Hello all,

Whenever I try wget I get this error:
> 
sam@sam-laptop:~$ wget google.com
--2010-06-29 10:54:58--  [http://google.com/](http://google.com/)
Resolving localhost... ::1, 127.0.0.1
Connecting to localhost|::1|:8080... failed: Connection refused.
Connecting to localhost|127.0.0.1|:8080... failed: Connection refused.


However my browser is working fine, and I can ping google.com
What can be wrong?

Thanks for any ideas!

---

### Post by mikewhatever on 2010-06-29
Wget is not a browser, it's a program for downloading files. Obviously, google.com is not a file, and hence the error.

---

### Post by TeoBigusGeekus on 2010-06-29
Maybe you should try 
```
wget www.google.com
```

---

### Post by nour02 on 2010-06-29
Hi, thanks for your answers.

wget [http://www.google.com](http://www.google.com) and wget [www.google.com](www.google.com) gives me the same error.

[http://ubuntuforums.org/showthread.php](http://ubuntuforums.org/showthread.php) is a file right? it won't download it either:

> sam@sam-laptop:~$ wget [http://ubuntuforums.org/showthread.php](http://ubuntuforums.org/showthread.php)
--2010-06-29 11:58:32--  [http://ubuntuforums.org/showthread.php](http://ubuntuforums.org/showthread.php)
Resolving localhost... ::1, 127.0.0.1
Connecting to localhost|::1|:8080... failed: Connection refused.
Connecting to localhost|127.0.0.1|:8080... failed: Connection refused.

---

### Post by mikewhatever on 2010-06-29
Indeed, it is a file. Somehow, instead of resolving ubuntuforums.org you get bounced to localhost. Are you directly connected to a modem/router?

---

### Post by DaithiF on 2010-06-29
is there a proxy defined thats routing every request through localhost?

try:
```
wget --no-proxy www.google.com
```

---

### Post by nour02 on 2010-06-29
Thanks DaithiF. The --no-proxy argument fixed my problem!

---

