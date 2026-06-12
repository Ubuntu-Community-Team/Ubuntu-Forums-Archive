---
title: "Domain name problems"
date: 2006-02-24
forum: General Help
---

### Post by jpbleuu on 2006-02-24
i'm at work here and we are testing out ubuntu on a computer, with the possibility of switchign over to this instead of using windows. now when i go into network settings and enter in a domain name i click ok it stays there until i reboot. is there a way to make this stay. essentially what i am looking for is when i go to connect to a shared folder on a windows pc i would like the domain name to come up instead of mshome. 

any thoughts?

---

### Post by lamego on 2006-02-24
I am not sure on this, but I believe it uses the samba configuration for that.
From a terminal type:
```
sudo gedit /etc/samba/smb.conf
```

---

