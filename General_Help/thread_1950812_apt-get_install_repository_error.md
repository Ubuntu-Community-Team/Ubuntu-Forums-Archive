---
title: "apt-get install repository error"
date: 2012-04-01
forum: General Help
---

### Post by steveray100 on 2012-04-01
I just ran apt-get update and I received the following error:

W: Failed to fetch [http://ubuntu.washdc-linux.com/ubuntu/dists/lucid-updates/restricted/source/Sources.gz](http://ubuntu.washdc-linux.com/ubuntu/dists/lucid-updates/restricted/source/Sources.gz)  Something wicked happened resolving 'ubuntu.washdc-linux.com:http' (-5 - No address associated with hostname)


any suggestions?

---

### Post by codemaniac on 2012-04-01
Hello , can you post your sources list?

---

### Post by codemaniac on 2012-04-01
I you have messed up your sources list , the below link might help you recreate one .
[http://repogen.simplylinux.ch/index.php](http://repogen.simplylinux.ch/index.php)

---

### Post by jerrrys on 2012-04-01
To post your sources list, open a terminal and enter:

cat -n /etc/apt/sources.list

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

