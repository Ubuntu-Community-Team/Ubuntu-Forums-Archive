---
title: "chmod not working, rkhunter install"
date: 2011-03-08
forum: General Help
---

### Post by Sethun on 2011-03-08
sudo: /etc/sudoers is mode 0777, should be 0440
sudo: no valid sudoers sources found, quitting

Is the message I'm getting.

---

### Post by Habitual on 2011-03-08
Changing the permissions gives you this "error"?
else you should:
```
sudo chmod 0440 /etc/sudoers
```

---

### Post by tordeu on 2011-03-08
There is a thread named "sudoers is mode 0777, should be 0440":

[http://ubuntuforums.org/showthread.php?t=237527&page=2](http://ubuntuforums.org/showthread.php?t=237527&page=2)

Try the first comment on this second page. This should get rid of the problem.

---

