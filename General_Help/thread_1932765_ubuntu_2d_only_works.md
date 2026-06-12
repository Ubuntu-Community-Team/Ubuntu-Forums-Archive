---
title: "ubuntu 2d only works"
date: 2012-02-28
forum: General Help
---

### Post by @yurfavproducer on 2012-02-28
I can only use ubuntu as well as the other derivatives kubuntu , etc in 2d ? 
I don't know why I think maybe it has something to do with my laptop's graphic card ?
I have a  Dell Inspiron m5030

When I type```
 lspci | grep VGA
``` into the terminal I get :


```
schinoxl@ubuntu:~$ lspci | grep VGA
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS880M [Mobility Radeon HD 4200 Series]
```

---

### Post by plucky on 2012-02-28
> **@yurfavproducer said:**
> I can only use ubuntu as well as the other derivatives kubuntu , etc in 2d ? 
I don't know why I think maybe it has something to do with my laptop's graphic card ?
I have a  Dell Inspiron m5030

When I type```
 lspci | grep VGA
``` into the terminal I get :


```
schinoxl@ubuntu:~$ lspci | grep VGA
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS880M [Mobility Radeon HD 4200 Series]
```

Have you tried selecting **System Settings > Additional Drivers** to see if the system installs drivers for your video hardware?

---

