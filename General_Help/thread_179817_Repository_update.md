---
title: "Repository update"
date: 2006-05-20
forum: General Help
---

### Post by ububaba on 2006-05-20
I am trying to update the repository by using the latest source.list and get the 
following result:

[PHP]$ sudo apt-get update
Err http://security.ubuntu.com breezy-security Release.gpg
  Could not connect to 172.16.1.71:8080 (172.16.1.71), connection timed out
Err http://archive.ubuntu.com breezy Release.gpg
  Could not connect to 172.16.1.71:8080 (172.16.1.71), connection timed out
Err http://archive.ubuntu.com breezy-updates Release.gpg
  Could not connect to 172.16.1.71:8080 (172.16.1.71), connection timed out
0% [Connecting to 172.16.1.71 (172.16.1.71)]
[/PHP]
Presumably, 172.16.1.71:8080 is not correct. Anyone knows the right one? Thanks.:-|

---

### Post by barbarian on 2006-05-20
Hei,
Do U want to upgrade to Dapper or just get the security Breezy updates? Btw, probably servers is really unreachable for the moment..

here some info that might be useful:

[https://wiki.ubuntu.com/AddingRepositoriesHowto?highlight=%28breezy%29%7C%28repositories%29](https://wiki.ubuntu.com/AddingRepositoriesHowto?highlight=%28breezy%29%7C%28repositories%29)

---

### Post by ububaba on 2006-05-20
[QUOTE=barbarian]Hei,
Do U want to upgrade to Dapper or just get the security Breezy updates? Btw, probably servers is really unreachable for the moment..

here some info that might be useful:

[https://wiki.ubuntu.com/AddingRepositoriesHowto?highlight=%28breezy%29%7C%28repositories%29](https://wiki.ubuntu.com/AddingRepositoriesHowto?highlight=%28breezy%29%7C%28repositories%29)[/QUOTE]

Thanks for the reply.   I have been having this problem for quite sometime.
I thought of waiting for sometime more before venturing into installing
Dapper.

---

### Post by barbarian on 2006-05-20
yes, it almost 10 days remaining, worth to wait;)

---

### Post by 3rdalbum on 2006-05-21
Some people are having repository problems at the moment, I had those kinds of problems about a week ago. I think they're having some rolling downtime in preparation for June.

---

### Post by Slim Odds on 2006-05-21
[QUOTE=ububaba]Presumably, 172.16.1.71:8080 is not correct. Anyone knows the right one? Thanks.:-|[/QUOTE]

172.16.X.X is a private address space and port 8080 usually indicates that a proxy server is being used.

This all means that you have a problem on your local network.

---

### Post by ububaba on 2006-05-21
[QUOTE=Slim Odds]172.16.X.X is a private address space and port 8080 usually indicates that a proxy server is being used.

This all means that you have a problem on your local network.[/QUOTE]

Thanks Slim. It was most likely a wrong step that I configured **[COLOR="Red"]apt.conf [/COLOR]**, as I am the 
sole user, thus there should no need for this:```
 ACQUIRE {
http::proxy "http://172.16.X.X:8080/"
}

``` Would you know where can changes be done so as not to prompt the usage of a proxy server?:-k

---

### Post by ububaba on 2006-05-21
> [QUOTE=ububaba]Thanks Slim. It was most likely a wrong step that I configured **[COLOR="Red"]apt.conf [/COLOR]**, as I am the 
sole user, thus there should no need for this:[CODE] ACQUIRE {
http::proxy "http://172.16.X.X:8080/"
}
Thanks everyone for the suggestions. I commented out ACQUIRE prompt and that did 
the trick.\\:D/ \\:D/

---

