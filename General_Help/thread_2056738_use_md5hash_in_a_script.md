---
title: "use md5hash in a script"
date: 2012-09-12
forum: General Help
---

### Post by nagileon on 2012-09-12
Hi there.
I know how to hash a string:


echo "MyPasswd123"|md5sum
3e043cc9d52d411fe0bfd674db0df3ef  -

Will linux understand when I use the password as follows:

ssh root:"3e043cc9d52d411fe0bfd674db0df3ef"@myserver.com

?

---

### Post by dodo3773 on 2012-09-12
Do not understand the question at all. Is this question actually about ssh?

---

### Post by tienlbhoc on 2012-09-12
do you want to use password protected by md5 ?

---

### Post by papibe on 2012-09-12
Hi nagileon.

That won't work, but you may want to check 'sshpass'. For instance:
```
shpass -p 'MyPasswd123' ssh username@@myserver.com
```

But even though that does it for you, the best way to script unattended ssh/rsync commands is to create [SSH Public and Private Keys]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys").

Regards.

---

