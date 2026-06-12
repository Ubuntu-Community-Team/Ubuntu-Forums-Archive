---
title: "GPG error report:: NO PUBLIC KEY"
date: 2010-05-29
forum: General Help
---

### Post by calvinfreakme on 2010-05-29
heyy guys...iam a newhere here..!   yestrday..when i tried to update my package manager i came across a error report..    

i hav taken d screenshot... i hav no idea wht it means...please help me out!



[IMG]http://lh5.ggpht.com/_5Vk2bhTFd3g/TADNMfR_QKI/AAAAAAAAC28/0_AK8I7DWXQ/s800/Screenshot.jpg[/IMG]

---

### Post by sisco311 on 2010-05-29
You have to add the public keys of the ppa repositories to the list of trusted keys. Open a terminal and run:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4e5e17b5 7fac5991
```

[https://launchpad.net/+help/soyuz/ppa-sources-list.html](https://launchpad.net/+help/soyuz/ppa-sources-list.html)

---

### Post by calvinfreakme on 2010-05-30
ok.. thanx!

---

