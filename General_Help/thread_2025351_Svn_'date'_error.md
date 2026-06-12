---
title: "Svn 'date' error"
date: 2012-07-14
forum: General Help
---

### Post by sdpagent on 2012-07-14
Dear all,
Whenever I try to get the log of a versioned directory/file, I get the following error message from svn (using rabbit vcs client)
[IMG]http://www.uploadscreenshot.com/image/1199479/5394856[/IMG]
[IMG]http://img1.uploadscreenshot.com/images/orig/7/19502221718-orig.jpg[/IMG]

Does anyone know how to fix this issue. This is the first time that I have come across it. I can checkout repositories fine, and commit to them, but can no longer go through the logs to check changes etc, which ruins the whole point of svn.

Stu

---

### Post by sdpagent on 2012-07-15
After rebooting the server and changing the configuration files to allow annonymous users that ability to read the files, the issue goes away, and I can read through the logs again. This is not ideal, as I dont want non-authenticated users to be able to read my code.

had to change the authz file from:
```
*= 
$authenticated = rw
```

to:

```
*= r
$authenticated = rw
```

and uncommented this line in svnserve.conf
```
#anon-access = read
```

---

