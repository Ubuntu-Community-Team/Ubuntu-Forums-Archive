---
title: "how to do apt-get update without proxy?"
date: 2011-07-13
forum: General Help
---

### Post by trevor_obba on 2011-07-13
Our proxy server has been decommissioned because our network has been configured so that every machines can get to the internet through the firewall.
  I am able to do “wget [http://www.google.com]("http://www.google.com/")” successfully
  
However, I configured apt not to use proxy setting in /etc/apt/apt.conf
  Like 
  Acquire::http::Proxy "false";



And in /etc/environment file
  http_proxy=""
  https_proxy=""


   When I try to do ubuntu update using “apt-get update” 

  I get the following error
    apt-get update
  Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
    Connection failed [IP: 91.189.92.166 80]
  Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy Release.gpg                          
    Connection failed
  Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_GB           
    Connection failed [IP: 91.189.92.166 80]
   
   
  How do I configure apt not to use proxy so that i could get ubuntu updates using “apt-get update”?

---

### Post by Toz on 2011-07-13
Try commenting out the Acquire::http:Proxy line /etc/apt/apt.conf as opposed to setting it to false. Also, before running apt-get update, check what you get with:```
echo $http_proxy
```Maybe the variable is set somewhere else like ~/.bashrc.

---

### Post by trevor_obba on 2011-07-14
echo $http_proxy shows nothing.

i also the deleted the containt of /etc/apt/apt.conf

however did not work, i am still geting error messages

Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
  Connection failed [IP: 91.189.92.166 80]
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy Release.gpg                          
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_GB           
  Connection failed [IP: 91.189.92.166 80]
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Translation-en_GB                  
  Connection failed


Can you help? please

---

### Post by CatKiller on 2011-07-14
> **trevor_obba said:**
> 
And in /etc/environment file
  http_proxy=""
  https_proxy=""


Try commenting out or removing those lines.

---

### Post by trevor_obba on 2011-07-14
Thanks it fixed.

it is, the next generation of firewall preventing from working, Once apt-get was added the firewall policy it started working.

Thanks again

---

