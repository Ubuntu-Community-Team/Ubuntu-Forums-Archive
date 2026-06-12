---
title: "How To enable Http Proxy Access While In Secure Shell"
date: 2009-08-19
forum: General Help
---

### Post by carloc on 2009-08-19
Hi,

I have this problem in which I cannot access the http proxy when i'm using secure shell.
I can access it properly when i use xrdp to login

but when i use secure shell to login, the http proxy cannot be used.

When I use ubuntu server, it can access the proxy properly but when i'm using ubuntu desktop, i can't seem to make it use the http proxy.

I'm trying to issue a

```
administrator@sxi-ubuntu2:~/sudo apt-get update
```but it results into errors in fetching updates coming from the repository.
I'm trying to connect to a proxy server which is 192.168.1.1 server.

It can't seem to access it, although when i try to echo the $http_proxy, i can see the proxy

```

administrator@sxi-ubuntu2:/etc/apt$ echo $http_proxy
192.168.1.1:75

```

---

### Post by carloc on 2009-08-19
I'm getting this error btw,
> 
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release.gpg
  Cannot initiate the connection to 75:80 (0.0.0.75). - connect (22 Invalid argument)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Translation-en_PH
  Cannot initiate the connection to 75:80 (0.0.0.75). - connect (22 Invalid argument)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Translation-en_PH
  Cannot initiate the connection to 75:80 (0.0.0.75). - connect (22 Invalid argument)

---

