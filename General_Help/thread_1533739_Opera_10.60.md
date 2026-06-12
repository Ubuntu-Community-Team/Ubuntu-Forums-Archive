---
title: "Opera 10.60"
date: 2010-07-18
forum: General Help
---

### Post by mdnw on 2010-07-18
Hello people,
Many moons ago I installed ubuntu and got so frustrated with my inability to use it as readily as I use windows I uninstalled said OS and went back over to the dark side. 
I have again seen the light and am now truly determined to stick with it this time but alas my new journey hasn't gone as planned and I have hit a opera shaped problem namely this

I installed opera using tar.gz not deb and I cannot uninstall  for the life of me I have tried everything I know ( which I admit isn't really that much ) I just cannot get rid its not in my Synaptic Package Manager and when I tried to purge it says not installed but it is because it I can use it.
Please help and thanks in advance.
Regards

---

### Post by sisco311 on 2010-07-18
Hi,

Open a terminal (Applications -> Accessories) and run:
```
sudo /usr/local/bin/uninstall-opera
```

---

### Post by crichard on 2010-07-18
Most probably, you moved opera folder into /opt directory. you can simply delete that opera folder from that directory. Try this following command to get admin access,

> gksudo nautilus


Install opera from deb version. That's it.

---

### Post by mdnw on 2010-07-18
daddy@Bertha:~$ sudo /usr/local/bin/uninstall-opera
sudo: /usr/local/bin/uninstall-opera: command not found
daddy@Bertha:~$ 

I will learn and I'm gonna make sure I enjoy myself in doing so

---

