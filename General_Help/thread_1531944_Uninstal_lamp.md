---
title: "Uninstal lamp"
date: 2010-07-15
forum: General Help
---

### Post by 1Nick1 on 2010-07-15
I do not know if this is the right section but anyway..
I need to uninstall Lamp from my Ubuntu 10.04 OS.
I just need to commands etc as I am rather noob at Ubuntu.
I will be installing it again I just have come across several problems. Thanks.

---

### Post by 1Nick1 on 2010-07-15
Can anyone help me? I have tried lots of things

---

### Post by bodhi.zazen on 2010-07-15
first, please do not bump your own threads in less then 24 hours minimum, 10 minutes is considered extremely rude.

Second, I assume you want to remove amp, if you want to remove the L , reinstall a new OS.

LAMP usually = Linux Apache Mysql and PHP

```
sudo apt-get -y purge php5 mysql apache2
```

You can also open synaptic and find and completely remove these packages.

[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

