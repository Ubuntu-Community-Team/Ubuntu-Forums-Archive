---
title: "Help with apache"
date: 2012-03-17
forum: General Help
---

### Post by AADAS on 2012-03-17
How to install the LATEST version of apache ?

---

### Post by jquis8411 on 2012-03-17
What's wrong with apt-get  apache? It's probably your best bet.

---

### Post by AADAS on 2012-03-17
Install version 2.2 not version 2.4

---

### Post by codemaniac on 2012-03-17
Repos often try to provide the last stable versions . If you want the latest bleeding edge versions , you need to dounload the souce tarballs from apache website .
[http://httpd.apache.org/download.cgi]("http://httpd.apache.org/download.cgi")

---

### Post by AADAS on 2012-03-17
Ok but I am stuck on this step:
./configure -- prefix=/usr/local/apache2
It says that i need to install arp-util

---

### Post by codemaniac on 2012-03-17
Please read carefully the README manual which is inside the tar archive before proceeding .

---

### Post by codemaniac on 2012-03-17
seems like **arp-util** package is missing on your ubuntu system .I guess you need to install it in order to hop the dependency hurdle .

---

### Post by AADAS on 2012-03-17
But how to install APR

---

### Post by codemaniac on 2012-03-17
find them in the repos and install .If it is not available in the repos then you need to do an source installation as you are doing for apache .

try searching it in repos
```
sudo apt-cache search arp-util
```

if available then install it .

---

### Post by codemaniac on 2012-03-17
Also you need to know which version of arp-util is needed for apache server (2.4) .That is why reading the README file is vital , it would be helpful if you could grep some time out and have a look at it .Best of Luck .

---

