---
title: "finding out whether other users are logged in?"
date: 2010-02-16
forum: General Help
---

### Post by V for Vincent on 2010-02-16
Hey there. Something's been bothering me for a while. Whenever I want to shut down, I have to enter my password, because shutting down while other users are logged in is a privileged operation. Now, I couldn't download an update because the update lock was in use. I'd be surprised if someone had targeted my system, especially because I didn't install any obscure .debs or anything recently, but I'd really like to find out if it's been compromised somehow. Say, by obtaining an overview of all users currently logged into my system or something. Is that possible?

---

### Post by Satoru-san on 2010-02-16
```
who
```very nice output

```
users
```one line

You might want to 

```
sudo cat /var/log/auth.log | tail -n 20
```

This will show you all log in attempts

---

### Post by V for Vincent on 2010-02-16
Thanks, turned out it was a legitimate program running with privileges.

---

