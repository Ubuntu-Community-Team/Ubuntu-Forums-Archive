---
title: "How to use HTTP proxy in Ubuntu Software Center"
date: 2012-06-13
forum: General Help
---

### Post by ashhab2010 on 2012-06-13
Well as said in the title i cannot use proxy with Software center. I have read at some places that i need to edit a config file but i dont know which one.

---

### Post by raja.genupula on 2012-06-13
open your terminal and do as 

```
gksu gedit /etc/apt/apt.conf
```

then place the format of your proxy like this ```
Acquire::http::proxy "http://user:pass@host:port/";
```

Hope that helps.:)

---

### Post by lunamystry on 2012-06-13
I usually set my proxy in two places and it works:

~/.bashrc (I only have one user on my PC, if you have more, you may wanna use /etc/bash.bashrc)
```
export http_proxy="http://<username>:<password>@<hostname>:<port>"
export ftp_proxy="http://<username>:<password>@<hostname>:<port>"
export https_proxy="http://<username>:<password>@<hostname>:<port>"
```

Then for apt:
/etc/apt/apt.conf
```
Acquire::http::proxy "http://<username>:<password>@<hostname>:<port>/";
Acquire::https::proxy "http://<username>:<password>@<hostname>:<port>/";
Acquire::ftp::proxy "http://<username>:<password>@<hostname>:<port>/";
```

I think you probably just need the apt.conf one. Just pay attention to the colons. 

Explaination:
The first one sets environment  variables {http,ftp,https}_proxy, a lot of terminal apps (eg wget) and some gui apps use these variables for proxy settings.
The second one sets the proxy settings for apt, which I think is the backend that the software center uses. 
The problem I had was that editing the proxy through the Ubuntu GUI that they provide, did not set the password and I would get proxy authentication errors. The above solved it for me. 

Scolding:
You should use google and search the forum before you post a question. example [https://help.ubuntu.com/community/AptGet/Howto]("https://help.ubuntu.com/community/AptGet/Howto") if you scroll to the bottom. 

Hope this helps,
Mandla

---

