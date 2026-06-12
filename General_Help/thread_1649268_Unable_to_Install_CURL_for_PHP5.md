---
title: "Unable to Install CURL for PHP5"
date: 2010-12-20
forum: General Help
---

### Post by cancer10 on 2010-12-20
Hi

I am following [this]("http://me.jacobwg.com/157-setup-php-5-and-curl-in-ubuntu-10-04") tutorial and thus running the following command to install curl for php5

```
sudo apt-get install curl libcurl3 libcurl3-dev php5-curl php5-mcrypt
```


But getting this error

```

rabbit@ubuntu:~$ sudo apt-get install curl libcurl3 libcurl3-dev php5-curl php5-mcrypt
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libcurl3 is already the newest version.
Note, selecting libcurl4-openssl-dev instead of libcurl3-dev
php5-mcrypt is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libcurl4-openssl-dev: Depends: libssl-dev but it is not going to be installed
  php5-curl: Depends: php5-common (= 5.3.2-1ubuntu4) but 5.3.2-1ubuntu4.5 is to be installed
E: Broken packages
rabbit@ubuntu:~$ 


```


Please if anyone can help me.

FYI - I am using Ubuntu 10.04


Many thanks

---

