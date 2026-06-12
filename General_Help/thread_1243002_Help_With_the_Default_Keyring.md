---
title: "Help With the Default Keyring"
date: 2009-08-17
forum: General Help
---

### Post by kyle2595 on 2009-08-17
For some reason, when I type in my Default Keyring / Sudo password (when I run Evolution and other programs that ask for it), it tells me that it is wrong. I know that it is the correct password though. I may have done something to change it without realizing it, so how can I change it back to what I want? Thank you and please excuse my lack of knowledge.

---

### Post by michy99 on 2009-08-17
Have you changed your log-in password?

---

### Post by kyle2595 on 2009-08-17
No, the log - in password is the same as it has always been.

---

### Post by jeffmodern on 2009-08-17
> **michy99 said:**
> Have you changed your log-in password?
Go to /usr/bin/ and locate the file nm-connection-editor and change the permission to 777 or 755 if you wish. the 777 means you are given right to all user while the 755 means that the root user has all right while other users do not.
Try this out and if it request for password again, run it without the username.

---

### Post by kyle2595 on 2009-08-17
That brings up the Network Connection editor, how do you change permissions?

---

### Post by kyle2595 on 2009-08-17
Never mind, I finally found this:
[http://www.code-muse.com/blog/?p=53](http://www.code-muse.com/blog/?p=53)
It helps a lot.

---

