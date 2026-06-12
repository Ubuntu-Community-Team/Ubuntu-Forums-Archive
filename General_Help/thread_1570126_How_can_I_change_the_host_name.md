---
title: "How can I change the host name ?"
date: 2010-09-07
forum: General Help
---

### Post by binarylife on 2010-09-07
Hi ,
Can I change the Host name ?

---

### Post by chopinhauer on 2010-09-07
```
sudo -i
echo your_new_hostname >/etc/hostname
hostname -F /etc/hostname

```

---

### Post by stevebu56 on 2010-09-07
This thread talks about your question. 
[Changing the hostname]("http://ubuntuforums.org/showthread.php?t=1004500")

---

