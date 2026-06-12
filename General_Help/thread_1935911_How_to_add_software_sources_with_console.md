---
title: "How to add software sources with console"
date: 2012-03-05
forum: General Help
---

### Post by lonekingc4 on 2012-03-05
Hi. I recently installed Ubuntu Server 11.10. But I cannot install any software using the "apt-get" command. I think that's because the software sources for my country (Bangladesh) don't really work. 

In Ubuntu 11.10 I managed to change the sources from the software center. I use Ubuntu main server as the source and it works. But how can I change the source in Ubuntu Server edition with only the command line? I am fairly new to the Linux world so please give me a step by step instruction :D Thanks.

---

### Post by howefield on 2012-03-05
The path to your sources.list is /etc/apt/sources.list so use your favourite text editor to open it up and amend as required.

```
sudo nano /etc/apt/sources.list
```

See also : [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

---

### Post by lonekingc4 on 2012-03-05
> **howefield said:**
> The path to your sources.list is /etc/apt/sources.list so use your favourite text editor to open it up and amend as required.

```
sudo nano /etc/apt/sources.list
```

See also : [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

Thanks. But what is the exact line I need to add for the Ubuntu main server repository?
Ok I have found another way. As the source.list file in my normal Ubuntu is working fine, I will just copy this file and replace the one in the Ubuntu Server. This should work, right?

---

### Post by raja.genupula on 2012-03-05
[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

please look at that may be it could help you . 

all the best .

---

### Post by lonekingc4 on 2012-03-05
> **raja.genupula said:**
> [http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

please look at that may be it could help you . 

all the best .

Superb! Thanks a lot :D

---

### Post by raja.genupula on 2012-03-05
Welcome man :)

---

